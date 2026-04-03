getwd()
setwd("C:/Users/ASUS/Documents/timeseries")

#Nama: Salsabila Ramadhani
#NIM: 23106010055
#Mata Kuliah: Analisis Runtun Waktu
#Tugas 7

data = read.csv("data_timeseries_salsa.csv", sep = ",", nrows = 20)
data

y_t = as.numeric(gsub(",", ".", data[[2]]))
y_hat = as.numeric(gsub(",", ".", data[[3]]))

y_t = na.omit(y_t)
y_hat = na.omit(y_hat)

n = min(length(y_t), length(y_hat))
y_t = y_t[1:n]
y_hat = y_hat[1:n]

#Perhitungan
e_t = y_t - y_hat
PE_t = (e_t / y_t) * 100

ME = mean(e_t)
MAD = mean(abs(e_t))
MSE = mean(e_t^2)
MPE = mean(PE_t)
MAPE = mean(abs(PE_t))

hasil_evaluasi = data.frame(
  Ukuran = c("ME", "MAD", "MSE", "MPE (%)", "MAPE (%)"),
  Nilai = c(ME, MAD, MSE, MPE, MAPE)
)

print(hasil_evaluasi)

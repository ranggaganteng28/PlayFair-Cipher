# PLAYFAIR-CIPHER-PYTHON-

| Rangga Saputra        |     312010266         |
|-----------------------|-----------------------|
|    TI.20.A.2          |     KRIPTOGRAFI       |
|   PERTEMUAN 6         |   PlayFair-Cipher     |

## Penjelasan tentang PLAYFAIR CHIPHER
```
Metode Playfair Cipher
square adalah teknik enkripsi simetrik yang termasuk dalam sistem substitusi digraph. 
dipecahkan jika dibandingkan dengan sistem substitusi sederhana seperti caesar atau viginere.

DECRYPT SANDI 
Dekripsi adalah proses mengubah kata sandi (cipherteks) menjadi kata terang (plainteks). 
Proses dekripsi sangat mirip dengan proses enkripsi dan lebih mudah dilakukan. Untuk melakukan proses dekripsi, 
cipherteks dikelompokkan terlebih dahulu dalam pasangan huruf seperti pada saat enkripsi, kemudian menggunakan 
algoritme dekripsi yang merupakan kebalikan dari algoritme enkripsi untuk setiap pasangan huruf tersebut. 
```
## OUTPUT CAPTURE Hasil Enkripsi dan dekripsi

Soal Lakukan Enkripsi pada Plaintext 
  * GOOD BROOM SWEEP CLEAN
  * REDWOOD NATIONAL STATE PARK
  * JUNK FOOD AND HEALTH PROBLEMS
  
Tools yang saya pake yaitu : 
  * Visual Studio Code
  * PYTHON 
## Hasil enkripsi
* disini saya melakukan enkripsi dengan python
1. Buat lah codingan dengan nama file PlayFairCipher.py
* untuk codinganya seperti berikut
```
key=input("Masukkan Kata Kunci : ")
key=key.replace(" ", "")
key=key.upper()
def matrix(x,y,initial):
    return [[initial for i in range(x)] for j in range(y)]
    
result=list()
for c in key: 
    if c not in result:
        if c=='J':
            result.append('I')
        else:
            result.append(c)
flag=0
for i in range(65,91): 
    if chr(i) not in result:
        if i==73 and chr(74) not in result:
            result.append("I")
            flag=1
        elif flag==0 and i==73 or i==74:
            pass    
        else:
            result.append(chr(i))
k=0
my_matrix=matrix(5,5,0) 
for i in range(0,5): 
    for j in range(0,5):
        my_matrix[i][j]=result[k]
        k+=1

def locindex(c):
    loc=list()
    if c=='J':
        c='I'
    for i ,j in enumerate(my_matrix):
        for k,l in enumerate(j):
            if c==l:
                loc.append(i)
                loc.append(k)
                return loc
            
def encrypt():  
    msg=str(input("Masukkan Pesan : "))
    msg=msg.upper()
    msg=msg.replace(" ", "")             
    i=0
    for s in range(0,len(msg)+1,2):
        if s<len(msg)-1:
            if msg[s]==msg[s+1]:
                msg=msg[:s+1]+'X'+msg[s+1:]
    if len(msg)%2!=0:
        msg=msg[:]+'X'
    print("Hasil Decrypt : ",end=' ')
    while i<len(msg):
        loc=list()
        loc=locindex(msg[i])
        loc1=list()
        loc1=locindex(msg[i+1])
        if loc[1]==loc1[1]:
            print("{}{}".format(my_matrix[(loc[0]+1)%5][loc[1]],my_matrix[(loc1[0]+1)%5][loc1[1]]),end=' ')
        elif loc[0]==loc1[0]:
            print("{}{}".format(my_matrix[loc[0]][(loc[1]+1)%5],my_matrix[loc1[0]][(loc1[1]+1)%5]),end=' ')  
        else:
            print("{}{}".format(my_matrix[loc[0]][loc1[1]],my_matrix[loc1[0]][loc[1]]),end=' ')    
        i=i+2        
                 
def decrypt():  
    msg=str(input("Masukkan Pesan : "))
    msg=msg.upper()
    msg=msg.replace(" ", "")
    print("Hasil Encrypt : ",end=' ')
    i=0
    while i<len(msg):
        loc=list()
        
        loc=locindex(msg[i])
        loc1=list()
        loc1=locindex(msg[i+1])
        if loc[1]==loc1[1]:
            print("{}{}".format(my_matrix[(loc[0]-1)%5][loc[1]],my_matrix[(loc1[0]-1)%5][loc1[1]]),end=' ')
        elif loc[0]==loc1[0]:
            print("{}{}".format(my_matrix[loc[0]][(loc[1]-1)%5],my_matrix[loc1[0]][(loc1[1]-1)%5]),end=' ')  
        else:
            print("{}{}".format(my_matrix[loc[0]][loc1[1]],my_matrix[loc1[0]][loc[1]]),end=' ')    
        i=i+2        

while(1):
    print("\n=======================")
    print("   PROGRAM PLAY FAIR    ")
    print("=======================")
    choice=int(input("\n 1.Encryption \n 2.Decryption \n 3.Exit \n   \n Masukkan Perintah : "))
    if choice==1:
        encrypt()
    elif choice==2:
        decrypt()
    elif choice==3:
        exit()
    else:
        print("Tolong Pilih Perintah yang Benar")
```

2. Setelah itu kita jalankan tools nya yaitu kita pilih enkripsi no 1

![images](img/jalankan_program.JPG)

Sukses data terenkripsi ...

```
GOOD BROOM SWEEP CLEAN
>? CMRCDFRWRAPYKWOWBPIOKY 


REDWOOD NATIONAL STATE PARK
>? OKCXRWRCIMETMEFULNFIOWFMRK


JUNK FOOD AND HEALTH PROBLEMS
>? AZINORRCMIGBIOVFCUMRLVNOQY 
```


---
title: "[Python] Bin file to ascii"
date: 2009-11-09
forum: Programming Talk
---

### Post by elbarto_87 on 2009-11-09
Hi All,

I am taking part in another maths forum where the situation has come up to convert a binary file to a text file. I initially suggested python because I assumed there would be a suitable module out there but I am afraid I spoke to soon or haven't looked in the right places.

If someone could please take a look at the format of the .bin file and the desired resulting .txt file (we have the code to convert a single file only, but this is in fortran and we are trying to use python to convert multiple files) that would be greatly appreciated. I am just having trouble with where to look to convert a .bin file into a txt file with columns of integer values.

I have tried using the binascii module but I do not think this is the right module. I have changed the file extension to .doc so I could upload here. Any advice would be great.

Thank you,

Regards Elbarto


Fortran Code:
```
program:
implicit none
integer lat, lon, irec,x,y
real*4 bmap(180,90)
parameter(irec=180*90*4)
open(21,file=
& 'c_015.bip_c1.bin',
& access='direct',
& form='unformatted',
& recl=irec,status='old',err=999)
read(21,rec=1,err=999)
& ((bmap(lon,lat),lon=1,180),lat=1,90)
close(21)
open(31,file=
& 'c_015.bip_c1.txt',
& form='formatted')
do 123 y=1,90
write(31,30) (bmap(x,y),x=1,180)
30 Format(180F12.6)
123 continue
999 continue

stop
End
```

---

### Post by MindSz on 2009-11-09
I don't know about Python, but I have a small C program to read in some binary integers from bin_in.txt and write them out as text in ascii_out.txt

```
include <stdlib.h>
#include<stdio.h>

int integers[8192*4]; //4096*2*bytes_por_int
int i;

FILE *archivo;
FILE *salida;

int main(){

  archivo = fopen("bin_in.txt","r");
  salida = fopen("ascii_out.txt","w");

  for (i = 0; i<8192; i=i+4096)
    fread(integers, 1, 4096, archivo);

  for (i = 0; i<8192; i++){
    fprintf(salida, "%d", integers[i]);
    if((i%10) == 0) fprintf(salida, "\n");
    else fprintf(salida, " ");
  }

  return 0;
}

```

---

### Post by elbarto_87 on 2009-11-09
Thanks alot MindSz.

Using your code as a guide, I was able to make something that works. My values were infact floats as I found out later. My python skills are very average so if anyone wants to pick my code to pieces please feel free as I appreciate the feedback. 

```
import os
import struct
def convertFile(fname_in, fname_out):  
    fin = open(fname_in,'rb')
    fout = open(fname_out,'w')
    while 1:
        try:
            vals = tuple([struct.unpack('f',fin.read(4))[0] for i in range(15)])
            fout.write(15*'%0.0f    ' % vals)
        except:
            break       
    fout.close()
num_converted = 0
for fname in os.listdir(os.getcwd()):
    if os.path.isdir(fname):
        continue
    else:
        try:
            f,ext = fname.rsplit('.',1)
            if ext.lower() == 'bin':
                convertFile(fname,f + '.txt')
                print(fname + " converted to " + fname + ".txt")
                num_converted += 1
        except ValueError:
            pass
print(str(num_converted) + " file(s) converted...")
raw_input("Press Enter to Exit...")
```


Thanks again,

Elbarto

---


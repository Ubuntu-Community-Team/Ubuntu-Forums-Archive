---
title: "Matlab read malformed text file"
date: 2010-02-16
forum: Programming Talk
---

### Post by erotavlas on 2010-02-16
Hi,

I have a "malformed" text file: it is similar to a file .CSV, but Matlab can't read it automatically.
I have tried a lot of Matlab functions importdata, fopen, textscan etc. but I can't read the file

this is a subsection of the file
```

Forward
Packet,Sequence,Time stamp,Delta (ms),Jitter (ms),Skew(ms),IP BW (kbps),Marker,Status
976,61063,0,0.00,0.00,0.00,10.18,,[ Ok ],02/15/2010 14:58:29.639,1286
977,61064,0,0.26,0.02,-0.26,21.04,,[ Ok ],02/15/2010 14:58:29.639,1372
978,61065,0,0.23,0.03,-0.49,26.94,SET,Incorrect timestamp,02/15/2010 14:58:29.639,752
1004,61066,249000,212.21,159.68,2553.96,32.44,SET,[ Ok ],02/15/2010 14:58:29.852,701

```


Matlab code

```

fid = fopen('h263w.txt','r');

InputText=textscan(fid,'%s',2,'delimiter','\n'); % Read strings delimited by a carriage return

format = '%f %f %f %f %f %f %f %s %s %f %f';

i=1;   % Initialize block index
while (i ~=10) % For each block...

     A = textscan(fid, format, 'delimiter',',')
    for j=1:7
        data(i,j) = A(1,j);
    end
       
   
    i=i+1;
end
fclose(fid);


```

I would like to get a Nx7 matrix where N is the number of rows of the file and the columns are 7.
The code read well only the first line of values...Can you help me?

Matlab code

```

fid = fopen('h263w.txt','r');

InputText=textscan(fid,'%s',2,'delimiter','\n'); % Read strings delimited by a carriage return

format = '%f %f %f %f %f %f %f %s %s %f %f';

i=1;   % Initialize block index
while (i ~=10) % For each block...

     A = textscan(fid, format, 'delimiter',',')
    for j=1:7
        data(i,j) = A(1,j);
    end
        
    
    i=i+1;
end
fclose(fid);


```

I would like to get a Nx7 matrix where N is the number of rows of the file and the column are 7.
The code read well only the first line of values...Can you help me?

---

### Post by pbrane on 2010-02-16
I haven't used MATLAB in a number of years, but this Octave function does what you want. Maybe you can convert what code doesn't work to MATLAB.
```

fid = fopen(filename);
if (fid == -1)
  error('File open error');
end

j = 1;
% skip the first and seccond line, they don't contain the data we want.
line = fgetl(fid);
line = fgetl(fid);

while (!feof(fid))
  line = fgetl(fid);
  for k = 1:7
    [tmp, line] = strtok(line, ',');
    data(k,j) = str2num(tmp);
  endfor
  j = j + 1;
end
% convert the matrix from 7xN to Nx7
data = data';

fclose(fid);

```

---

### Post by erotavlas on 2010-02-17
> **pbrane said:**
> I haven't used MATLAB in a number of years, but this Octave function does what you want. Maybe you can convert what code doesn't work to MATLAB.
```

fid = fopen(filename);
if (fid == -1)
  error('File open error');
end

j = 1;
% skip the first and seccond line, they don't contain the data we want.
line = fgetl(fid);
line = fgetl(fid);

while (!feof(fid))
  line = fgetl(fid);
  for k = 1:7
    [tmp, line] = strtok(line, ',');
    data(k,j) = str2num(tmp);
  endfor
  j = j + 1;
end
% convert the matrix from 7xN to Nx7
data = data';

fclose(fid);

```


Thank you very much

I have solved in the following manner

```

fid = fopen('h263.txt','r');

%Forward
%Packet,Sequence,Time stamp,Delta (ms),Jitter (ms),Skew(ms),IP BW  (kbps),Marker,Status

i=1;
format = '%f %f %f %f %f %f %f %s %s %f %f';
while ~feof(fid)
    tline = fgetl(fid);
    A = textscan(tline, format, 'delimiter', ',');
    for j=1:7
        data(i,j) = A(1,j);
    end
    i=i+1;
end
fclose(fid);

```

your solutions is more elegant...

---


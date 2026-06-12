---
title: "plotting an unknown number of plots in gnuplot"
date: 2010-12-01
forum: Programming Talk
---

### Post by Peter.Paul on 2010-12-01
Hello Community,

I am quite new to Linux shell and I am experimenting a lot with shell and gnuplot. I have quite long txt files that I to put all these txt files into one folder and than get a plot out of it. So far, I got one plot for every file. A got one programm for a loop
```

for i in *.txt   
do 
     ./$1.sh $i
done

```
And another one that is actually plotting
```

gnuplot<<EOF
set terminal jpeg
set output '$1.jpg'
plot '$1.txt' u 8:10 w l title '$min.txt'; 
reset
EOF

```
Do you have an idea how I can make one plot for all the files in the folder? The number of files in the directory may vary.

---

### Post by Arndt on 2010-12-01
> **Peter.Paul said:**
> Hello Community,

I am quite new to Linux shell and I am experimenting a lot with shell and gnuplot. I have quite long txt files that I to put all these txt files into one folder and than get a plot out of it. So far, I got one plot for every file. A got one programm for a loop
```

for i in *.txt   
do 
     ./$1.sh $i
done

```
And another one that is actually plotting
```

gnuplot<<EOF
set terminal jpeg
set output '$1.jpg'
plot '$1.txt' u 8:10 w l title '$min.txt'; 
reset
EOF

```
Do you have an idea how I can make one plot for all the files in the folder? The number of files in the directory may vary.

Do you mean you want to give something like the following to gnuplot?

```
set terminal jpeg
set output '$1.jpg'
plot file1.txt,file2.txt,file3.txt u 8:10 w l title '$min.txt'; 
reset
```

(This may be partly nonsense - I don't use gnuplot much.)

I would create a temporary file and put the commands for gnuplot in it.

---

### Post by JakeFrederix on 2010-12-02
```

# write a gnuplot script
echo 'set terminal jpeg' >> my_plot.gps

# iterate over .txt files
for i in *.txt
do
    # create appropriate name for resulting image
    filename=`echo $i | sed 's/txt/jpg/'`

    # add seperate plots for each file
    echo "set output '$filename'" >> my_plot.gps
    echo "plot '$i' u 1:2 w l title 'data from $i'" >> my_plot.gps
    echo "reset" >> my_plot.gps
done

# call gnuplot
gnuplot my_plot.gps

# delete temporary file
rm my_plot.gps

```Store abovementioned code in a file (in the same directory as your data files), and call the script with the sh command.

You will need to tweak it to suit your data files.

---


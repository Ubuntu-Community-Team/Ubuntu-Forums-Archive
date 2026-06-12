---
title: "[SOLVED] Matlab - looping when importing data"
date: 2008-02-20
forum: Programming Talk
---

### Post by renzokuken on 2008-02-20
Hi all.

Firstly, sorry if this is a dumb question but it seems like it should be really simple, however, i'm stuck.

I'm trying to write an m-file to import data from a .csv file into matlab and plot it all out.

The CSV contains 201 columns, the first is the x-data (as are all the other 'odd' columns cos of the way the software stores the data....all the same though). All the even columns though are 100 different sets of y-data.

The script i've written below, imports the data from the file, then assigns the x values, and the even columns to y values in the form column 2 = y1, column 4 = y2, column 6 = y3 etc etc.

This works fine but it seems like a hell of alot of code for something so simple. Is it possible to use a 'for' loop to auto increment the y-suffix and also count every other column when importing from the file?

Hope this makes sense.

```

function absorbanceplot(filename)

data = load(filename);
x = data(:,1);
y1 = data(:,2);
y2 = data(:,4);
y3 = data(:,6);
y4 = data(:,8);
y5 = data(:,10);
y6 = data(:,12);
y7 = data(:,14);
y8 = data(:,16);
y9 = data(:,18);
y10 = data(:,20);
y11 = data(:,22);
y12 = data(:,24);
y13 = data(:,26);
y14 = data(:,28);
y15 = data(:,30);
y16 = data(:,32);
y17 = data(:,34);
y18 = data(:,36);
y19 = data(:,38);
y20 = data(:,40);
y21 = data(:,42);
y22 = data(:,44);
y23 = data(:,46);
y24 = data(:,48);
y25 = data(:,50);
y26 = data(:,52);
y27 = data(:,54);
y28 = data(:,56);
y29 = data(:,58);
y30 = data(:,60);
y31 = data(:,62);
y32 = data(:,64);
y33 = data(:,66);
y34 = data(:,68);
y35 = data(:,70);
y36 = data(:,72);
y37 = data(:,74);
y38 = data(:,76);
y39 = data(:,78);
y40 = data(:,80);
y41 = data(:,82);
y42 = data(:,84);
y43 = data(:,86);
y44 = data(:,88);
y45 = data(:,90);
y46 = data(:,92);
y47 = data(:,94);
y48 = data(:,96);
y49 = data(:,98);
y50 = data(:,100);
y51 = data(:,102);
y52 = data(:,104);
y53 = data(:,106);
y54 = data(:,108);
y55 = data(:,110);
y56 = data(:,112);
y57 = data(:,114);
y58 = data(:,116);
y59 = data(:,118);
y60 = data(:,120);
y61 = data(:,122);
y62 = data(:,124);
y63 = data(:,126);
y64 = data(:,128);
y65 = data(:,130);
y66 = data(:,132);
y67 = data(:,134);
y68 = data(:,136);
y69 = data(:,138);
y70 = data(:,140);
y71 = data(:,142);
y72 = data(:,144);
y73 = data(:,146);
y74 = data(:,148);
y75 = data(:,150);
y76 = data(:,152);
y77 = data(:,154);
y78 = data(:,156);
y79 = data(:,158);
y80 = data(:,160);
y81 = data(:,162);
y82 = data(:,164);
y83 = data(:,166);
y84 = data(:,168);
y85 = data(:,170);
y86 = data(:,172);
y87 = data(:,174);
y88 = data(:,176);
y89 = data(:,178);
y90 = data(:,180);
y91 = data(:,182);
y92 = data(:,184);
y93 = data(:,186);
y94 = data(:,188);
y95 = data(:,190);
y96 = data(:,192);
y97 = data(:,194);
y98 = data(:,196);
y99 = data(:,198);
y100 = data(:,200);




plot(x,y1,'r', x,y2,'g', x,y3,'b', x,y4,'y', x,y5,'m', x,y6,'c', x,y7,'r', x,y8,'g', x,y9,'b', x,y10,'y', x,y11,'m', x,y12,'c', x,y13,'r', x,y14,'g', x,y15,'b', x,y16,'y', x,y17,'m', x,y18,'c', x,y19,'r', x,y20,'g', x,y21,'b', x,y22,'y', x,y23,'m', x,y24,'c', x,y25,'r', x,y26,'g', x,y27,'b', x,y28,'y', x,y29,'m', x,y30,'c', x,y31,'r', x,y32,'g', x,y33,'b', x,y34,'y', x,y35,'m', x,y36,'c', x,y37,'r', x,y38,'g', x,y39,'b', x,y40,'y', x,y41,'m', x,y42,'c', x,y43,'r', x,y44,'g', x,y45,'b', x,y46,'y', x,y47,'m', x,y48,'c', x,y49,'r', x,y50,'g', x,y51,'b', x,y52,'y', x,y53,'m', x,y54,'c', x,y55,'r', x,y56,'g', x,y57,'b', x,y58,'y', x,y59,'m', x,y60,'c', x,y61,'r', x,y62,'g', x,y63,'b', x,y64,'y', x,y65,'m', x,y66,'c', x,y67,'r', x,y68,'g', x,y69,'b', x,y70,'y', x,y71,'m', x,y72,'c', x,y73,'r', x,y74,'g', x,y75,'b', x,y76,'y', x,y77,'m', x,y78,'c', x,y79,'r', x,y80,'g', x,y81,'b', x,y82,'y', x,y83,'m', x,y84,'c', x,y85,'r', x,y86,'g', x,y87,'b', x,y88,'y', x,y89,'m', x,y90,'c', x,y91,'r', x,y92,'g', x,y93,'b', x,y94,'y', x,y95,'m', x,y96,'c', x,y97,'r', x,y98,'g', x,y99,'b', x,y100,'y');

axis([300, 2500, -1, 8])
title('Absorbance spectrum')
xlabel('Wavelangth (nm)')
ylabel('Absorbance (A.U.)')


```

---

### Post by renzokuken on 2008-02-20
ok, i think i solved it

```
function absorbanceplot(filename)

data = load(filename);

x = data(:,1);

%a=[];

for i = 1:100
    plot(x,data(:,2*i),'r')
    hold on
end
```

feeling quite smug now

however, one problem, the third input 'r' staes to plot a red coloured line, which isnt very usefull when i have 100 plots on the same graph all coloured red. is there a way to randomise the colour of each line or set it sequentially? options are (ignore the . point o circle etc)

```

     y     yellow        .     point
     m     magenta       o     circle
     c     cyan          x     x-mark
     r     red           +     plus
     g     green         -     solid
     b     blue          *     star
     w     white         :     dotted
     k     black         -.    dashdot
  	                     --    dashed
```

---

### Post by WW on 2008-02-20
Try this:
```

function absorbanceplot(filename)
    data = load(filename);
    x = data(:,1);
    plot(x,data(:,2:2:end))
 
```

---

### Post by renzokuken on 2008-02-21
thats awesome, thanks, worked like a charm

---


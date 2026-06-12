---
title: "Conky's problem in Pangolin"
date: 2013-08-02
forum: New to Ubuntu
---

### Post by czgirb on 2013-08-02
The Conky was installed inmy Pangolin. And I used it before. But since I haven't find a match wallpaper in order to display my Conky. So:
* I compressed conky's file and move the RAR file in Video directory.
* Stratup Application > conky > remove

But now, I found the desired wallpaper and wish to have my Conky's back. So,
* I extract the RAR file and move the folder to Home directory.
* Startup Application > **name:** conky / **command:** conky / and leave the **comment:** section to be emptied
* restart the Ubuntu and NOTHING is happen

Ask a friend and they suggest me to add: 
> **comment: **sleep 10 && conky -c conkyconfig
but NOTHING is happen also.

Please guide me ...

**PS:**
in terminal, when I typed conky ... all informations are showed in terminal.

---

### Post by deadflowr on 2013-08-02
1)Where is the conky script located?
2)What is the conky scripts name?
3)post the output of the conky script.

The conky command "conky" looks first for the file .conkyrc in the users home folder.
If it can't find that then it looks for the file in the /etc directory conky folder.
the -c option tells it to look for whatever file you want, with whatever name you give it, as long as the file is a conky script.
But you need to give the full path to that file, and not just the name.
You probably already know that, so posting the conky script and where it's located will probably be the most helpful.

---

### Post by czgirb on 2013-08-02
> **deadflowr said:**
> 1)Where is the conky script located?
2)What is the conky scripts name?
3)post the output of the conky script.

The conky command "conky" looks first for the file .conkyrc in the users home folder.
If it can't find that then it looks for the file in the /etc directory conky folder.
the -c option tells it to look for whatever file you want, with whatever name you give it, as long as the file is a conky script.
But you need to give the full path to that file, and not just the name.
You probably already know that, so posting the conky script and where it's located will probably be the most helpful.

Oh my God! I'm just a newbie.
Regarding to your 3-questions ... I really don't know what it is ... SORRY
Would you mind to guide me in order to do that? Please ...

---

### Post by NikTh on 2013-08-02
Open a terminal (CTRL+ALT+T) and give the results of following command 
```
ls -a
``` 

Also you can start conky directly from the terminal and see if any error messages are there.. 
```
conky
``` 

Regards
 NikTh

---

### Post by deadflowr on 2013-08-02
In general, when you first install conky, a script is placed in the folder /etc/conky.
Usually called conky.conf.
When you run the program conky, if a personalize script called .conkyrc is not in the users home folder, the program defaults to the /etc/conky/conky.conf file.
The .conkyrc file is a hidden file so to find it in the home folder press ctrl+h.
A dot means the file/folder is hidden.
If you want to run a script which is not called .conkyrc, then you need to use the -c,--config option.
```
conky -c /path/to/file
```
Note the -c option needs the path to the file and not just the file name.

It probably be helpful to know what files you extracted from the RAR.
And where you put them.
It might also be helpful to post the output from when you run conky in the terminal.

---

### Post by czgirb on 2013-08-03
[SIZE=4]**@ NikTh**[/SIZE]

ls -a
```

czgirb@czgirb:~$ ls -a
.                           .goutputstream-I5APRW
..                          .goutputstream-I6T0JW
.adobe                      .goutputstream-I8NAKW
.aMule                      .goutputstream-IBGOJW
.audacity-data              .goutputstream-IOONTW
.avast                      .goutputstream-IVTFSW
.avidemux                   .goutputstream-IW59RW
backtrace.txt               .goutputstream-J1ACKW
.bash_history               .goutputstream-J73SJW
.bash_logout                .goutputstream-J82JPW
.bashrc                     .goutputstream-JCGYSW
.bcast                      .goutputstream-JID7PW
bd.key.asc                  .goutputstream-JOWJ0W
.cache                      .goutputstream-JPXP0W
Calibre Library             .goutputstream-JQKKRW
C:\nppdf32Log\debuglog.txt  .goutputstream-JW9HJW
.compiz-1                   .goutputstream-JWO7RW
.config                     .goutputstream-K05TRW
.conkyrc                    .goutputstream-K5QSYW
.dbus                       .goutputstream-K9GVGW
Desktop                     .goutputstream-KAJXMW
.dmrc                       .goutputstream-KCSVGW
Documents                   .goutputstream-KDKAJW
Downloads                   .goutputstream-KF16LW
examples.desktop            .goutputstream-KJLXGW
.face                       .goutputstream-KK7YQW
FFOutput                    .goutputstream-KPYETW
.fontconfig                 .goutputstream-KUSEHW
.Foxit                      .goutputstream-L1390W
FoxitReader                 .goutputstream-L2KHJW
.gconf                      .goutputstream-LD3TJW
.gegl-0.0                   .goutputstream-LJG9QW
.gimp-2.6                   .goutputstream-LK7CSW
.gksu.lock                  .goutputstream-LM2SOW
gmusicbrowser               .goutputstream-LMRA1W
.gnome                      .goutputstream-LNK9IW
.gnome2                     .goutputstream-LSDTHW
.gnome2_private             .goutputstream-LW16MW
.gnome-color-chooser        .goutputstream-LYKLHW
.goutputstream-01LUZW       .goutputstream-M0OVHW
.goutputstream-07FVJW       .goutputstream-M1UURW
.goutputstream-093FHW       .goutputstream-M1X3TW
.goutputstream-0CVGGW       .goutputstream-MD46GW
.goutputstream-0QD8UW       .goutputstream-MFVPXW
.goutputstream-0RHEMW       .goutputstream-MGVNQW
.goutputstream-0RPKHW       .goutputstream-MQ32RW
.goutputstream-0UBCRW       .goutputstream-MS7PJW
.goutputstream-0VI7OW       .goutputstream-MSFUJW
.goutputstream-0Y24JW       .goutputstream-MSK1YW
.goutputstream-130BKW       .goutputstream-MVJDHW
.goutputstream-132KXW       .goutputstream-MVLVMW
.goutputstream-15UJZW       .goutputstream-MW36UW
.goutputstream-18B7WW       .goutputstream-MXNNIW
.goutputstream-1AQIRW       .goutputstream-N21KRW
.goutputstream-1M2JLW       .goutputstream-N6NURW
.goutputstream-1M3LJW       .goutputstream-N7BFKW
.goutputstream-1MOJHW       .goutputstream-N7G6JW
.goutputstream-1OBWVW       .goutputstream-N8FLJW
.goutputstream-1OS8LW       .goutputstream-N98IRW
.goutputstream-1QINXW       .goutputstream-NG0JWW
.goutputstream-1WNNJW       .goutputstream-NG4XSW
.goutputstream-22K4VW       .goutputstream-NG7CIW
.goutputstream-264ATW       .goutputstream-NJLYKW
.goutputstream-27D4HW       .goutputstream-NKHQKW
.goutputstream-2903MW       .goutputstream-NM89IW
.goutputstream-29OXLW       .goutputstream-NU3FOW
.goutputstream-2C22KW       .goutputstream-NVULKW
.goutputstream-2HJLTW       .goutputstream-NZ2GSW
.goutputstream-2J58QW       .goutputstream-O1JGVW
.goutputstream-2KXVSW       .goutputstream-O23HJW
.goutputstream-2MH5MW       .goutputstream-O46GOW
.goutputstream-2R7MVW       .goutputstream-O9EDJW
.goutputstream-2S21MW       .goutputstream-OB9WLW
.goutputstream-2U7KHW       .goutputstream-OBM3QW
.goutputstream-3712LW       .goutputstream-ODENUW
.goutputstream-39GPLW       .goutputstream-OGYAOW
.goutputstream-3AFFIW       .goutputstream-OHXVKW
.goutputstream-3EO1IW       .goutputstream-OQ5IKW
.goutputstream-3JRFJW       .goutputstream-OR1GIW
.goutputstream-3JSFLW       .goutputstream-P02VQW
.goutputstream-3LBQTW       .goutputstream-P6ZVQW
.goutputstream-3OF6WW       .goutputstream-PN2FIW
.goutputstream-3T0UIW       .goutputstream-PN7UYW
.goutputstream-3UNAKW       .goutputstream-PTZ5QW
.goutputstream-3WM8JW       .goutputstream-PVGZRW
.goutputstream-4299MW       .goutputstream-PW4MMW
.goutputstream-46XCJW       .goutputstream-PYX2MW
.goutputstream-4JGURW       .goutputstream-Q1VHNW
.goutputstream-4VAFTW       .goutputstream-QBCZTW
.goutputstream-4VMCTW       .goutputstream-QIJ3NW
.goutputstream-4X8DHW       .goutputstream-QKTIRW
.goutputstream-55HIIW       .goutputstream-QL55ZW
.goutputstream-55SPMW       .goutputstream-QL8YKW
.goutputstream-579ZSW       .goutputstream-QX3JMW
.goutputstream-5BO0SW       .goutputstream-QZDZUW
.goutputstream-5BSALW       .goutputstream-QZR5WW
.goutputstream-5COWSW       .goutputstream-R1U5IW
.goutputstream-5E3GOW       .goutputstream-R1XAIW
.goutputstream-5FU2KW       .goutputstream-R1XBJW
.goutputstream-5QZQKW       .goutputstream-RBJ0QW
.goutputstream-5RBGHW       .goutputstream-RDSBJW
.goutputstream-5S8STW       .goutputstream-RLY9KW
.goutputstream-5XSQJW       .goutputstream-ROSMRW
.goutputstream-6314LW       .goutputstream-RTT1IW
.goutputstream-6KT4SW       .goutputstream-RU01LW
.goutputstream-6MCMTW       .goutputstream-S0ULNW
.goutputstream-6Q6BNW       .goutputstream-S5A5LW
.goutputstream-6VZ2TW       .goutputstream-S9UTLW
.goutputstream-6WBZNW       .goutputstream-SC9VMW
.goutputstream-70M0XW       .goutputstream-SD2ONW
.goutputstream-769CJW       .goutputstream-SHNCTW
.goutputstream-7CNEJW       .goutputstream-SJUYKW
.goutputstream-7H6ATW       .goutputstream-SPDZXW
.goutputstream-7IMYJW       .goutputstream-SPKYWW
.goutputstream-7JLYTW       .goutputstream-SQPGOW
.goutputstream-7N2RSW       .goutputstream-SSKUNW
.goutputstream-7NSIXW       .goutputstream-STKMJW
.goutputstream-7OE1SW       .goutputstream-SZUUWW
.goutputstream-7P0QGW       .goutputstream-T1LBQW
.goutputstream-7XOFNW       .goutputstream-T3OPLW
.goutputstream-7Y0MTW       .goutputstream-T51OTW
.goutputstream-89IVKW       .goutputstream-T6DYJW
.goutputstream-8DNFJW       .goutputstream-TCQRUW
.goutputstream-8FFJTW       .goutputstream-TCV5IW
.goutputstream-8LRBJW       .goutputstream-TDYNKW
.goutputstream-8MXNWW       .goutputstream-TEZ4UW
.goutputstream-8SQKKW       .goutputstream-TMZ5QW
.goutputstream-8W72KW       .goutputstream-TSQ0KW
.goutputstream-8WPSIW       .goutputstream-TT10IW
.goutputstream-90JRTW       .goutputstream-TVC7HW
.goutputstream-90YBGW       .goutputstream-U4APHW
.goutputstream-95L6RW       .goutputstream-U55BVW
.goutputstream-95TLTW       .goutputstream-U5U7RW
.goutputstream-95UNLW       .goutputstream-UB19IW
.goutputstream-9BXTRW       .goutputstream-UEU4OW
.goutputstream-9D9ALW       .goutputstream-UI0ZQW
.goutputstream-9HYSSW       .goutputstream-UO7QNW
.goutputstream-9M6BTW       .goutputstream-USI9LW
.goutputstream-9R5DTW       .goutputstream-UV6GMW
.goutputstream-9WA5KW       .goutputstream-V5G0JW
.goutputstream-9XM4MW       .goutputstream-VHTAWW
.goutputstream-9ZBOJW       .goutputstream-VQMQRW
.goutputstream-A2JPRW       .goutputstream-VRIBKW
.goutputstream-A3O5KW       .goutputstream-VRSTVW
.goutputstream-A65ZKW       .goutputstream-VTFUJW
.goutputstream-AAZ6GW       .goutputstream-VURRJW
.goutputstream-AFOGJW       .goutputstream-VX21UW
.goutputstream-AJE5HW       .goutputstream-VZQ8RW
.goutputstream-AX3LLW       .goutputstream-VZQILW
.goutputstream-B1A4JW       .goutputstream-W29ZTW
.goutputstream-BAHNTW       .goutputstream-W4ALLW
.goutputstream-BCCQTW       .goutputstream-W50RHW
.goutputstream-BLRYSW       .goutputstream-W5LKVW
.goutputstream-BO2FRW       .goutputstream-W94ITW
.goutputstream-BUEXPW       .goutputstream-WERGKW
.goutputstream-C6LPLW       .goutputstream-WH2EMW
.goutputstream-C79DUW       .goutputstream-WUJ3QW
.goutputstream-CAZSJW       .goutputstream-WYEKNW
.goutputstream-CE07IW       .goutputstream-X2HWUW
.goutputstream-CE2VHW       .goutputstream-X2V0LW
.goutputstream-CHC0QW       .goutputstream-X506RW
.goutputstream-CKXMJW       .goutputstream-X6LZJW
.goutputstream-CMT6SW       .goutputstream-XDJ0QW
.goutputstream-CQ5SNW       .goutputstream-XFYFGW
.goutputstream-CQ94PW       .goutputstream-XL66QW
.goutputstream-CTR2LW       .goutputstream-XQ2IVW
.goutputstream-CTYCHW       .goutputstream-XQT5QW
.goutputstream-CX96PW       .goutputstream-Y1MAKW
.goutputstream-D1I1HW       .goutputstream-Y2TDLW
.goutputstream-D4HVRW       .goutputstream-Y4SQHW
.goutputstream-D5F9QW       .goutputstream-YBSWRW
.goutputstream-D7GWGW       .goutputstream-YDQ5QW
.goutputstream-D8EFRW       .goutputstream-YI6EXW
.goutputstream-D9JHVW       .goutputstream-YMHCKW
.goutputstream-DA7CVW       .goutputstream-YOV9GW
.goutputstream-DLHBJW       .goutputstream-YU3INW
.goutputstream-DOB2RW       .goutputstream-YY5PNW
.goutputstream-DQOMUW       .goutputstream-Z1TUVW
.goutputstream-DRW9FW       .goutputstream-ZJDQPW
.goutputstream-DUP0RW       .goutputstream-ZJUPJW
.goutputstream-DX79QW       .goutputstream-ZMWBJW
.goutputstream-E2TAQW       .goutputstream-ZO1V0W
.goutputstream-E8Q6LW       .goutputstream-ZOIRUW
.goutputstream-EKEERW       .goutputstream-ZRY6MW
.goutputstream-ES36VW       .goutputstream-ZS0IMW
.goutputstream-EXARTW       .gstreamer-0.10
.goutputstream-EZONIW       .gtk-bookmarks
.goutputstream-F6RRVW       .gtkrc-2.0-gnome-color-chooser
.goutputstream-F9V8YW       .gvfs
.goutputstream-FBGGKW       .ICEauthority
.goutputstream-FC1QTW       .icons
.goutputstream-FCWNJW       .java
.goutputstream-FMFXHW       .kde
.goutputstream-FQOOWW       .launchpadlib
.goutputstream-FTGHSW       libpeerconnection.log
.goutputstream-FWDLVW       .local
.goutputstream-FYWMKW       .macromedia
.goutputstream-G2ODGW       .mateconf
.goutputstream-G3ZVVW       .mateconfd
.goutputstream-G9LRJW       .mission-control
.goutputstream-GA2PUW       .mozilla
.goutputstream-GBCEQW       Music
.goutputstream-GJ2TQW       .odbc.ini
.goutputstream-GJGYHW       .openoffice.org
.goutputstream-GJZFMW       Pictures
.goutputstream-GKMVIW       .pki
.goutputstream-GSB5WW       .PlayOnLinux
.goutputstream-GURPXW       .profile
.goutputstream-GX5WWW       Public
.goutputstream-GZZ9LW       .puddletag
.goutputstream-H34HTW       .pulse
.goutputstream-H4CQOW       .pulse-cookie
.goutputstream-H6CGMW       script.py
.goutputstream-H6LULW       .shotwell
.goutputstream-H9G7LW       .Skype
.goutputstream-HCKMQW       .sudoku
.goutputstream-HE0SWW       Templates
.goutputstream-HGB8NW       .themes
.goutputstream-HHMXQW       .thumbnails
.goutputstream-HHSSRW       .thunderbird
.goutputstream-HLSZJW       Ubuntu One
.goutputstream-HV2XRW       Videos
.goutputstream-HXBRRW       .wine
.goutputstream-HZ46KW       .Xauthority
.goutputstream-HZGXQW       .xinput.d
.goutputstream-HZKD0W       .xsession-errors
.goutputstream-I4UNRW       .xsession-errors.old
czgirb@czgirb:~$ 

```

[SIZE=4][B]@ NikTh & Deadflowr
[/B][/SIZE]
conky
> 
czgirb@czgirb:~$ conky
Conky: invalid configuration file '/home/czgirb/.conkyrc'

Conky: missing text block in configuration; exiting
czgirb@czgirb:~$ 


---

### Post by deadflowr on 2013-08-03
Firstly, you can delete all those goutputstream files.
It's a known bug.
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785)
those files are empty anyway so nothing will be lost.

Secondly, you have a .conkyrc file but as posted something's wrong.
Open that file with gedit, or other text editor and copy and post the results
It looks like something is broken in it.

---

### Post by NikTh on 2013-08-03
Let us see the contents of .conkyrc. 

```
cat .conkyrc
``` 

As for the goutputstream... files, as @deadflowr said, is a known bug. Create a script with following contents and put it in startup applications. 
```
#!/bin/bash 
curr=.goutputstream-*
 if [[ -e /home/czgirb/$curr ]]; then
 `rm .goutputstream-*`
 exit 0
else
 exit 1
fi

``` 
Lets name it **remove-polution.sh. **Now click startup applications and add new, at command write /home/czgirb/remove-polution.sh
Give executable permissions on script 
```
chmod +x remove-polution.sh
``` 

Regards 
NikTh

---

### Post by czgirb on 2013-08-03
[SIZE=3]**To: NikTh & Deadflowr**[/SIZE]

As requested:
```

background no
font Sans:size=8
#xftfont Sans:size=10
use_xft yes
xftalpha 0.9
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 220
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color green
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase

TEXT
${color white}SYSTEM ${hr 1}${color}

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Temp: ${alignr}${acpitemp}C

CPU: ${alignr}${freq} MHz
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

CPU1 ${alignr}${cpu cpu1}%
${cpubar 4 cpu1}
CPU2 ${alignr}${cpu cpu2}%
${cpubar 4 cpu2}

Ram ${alignr}$mem / $memmax ($memperc%)
${membar 4}
swap ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

${color white}Filesystem ${hr 1}${color}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /home}
HDD0: ${alignr}${fs_free /media/HDD0} / ${fs_size /media/HDD0}
${fs_bar 4 /media/HDD0}
HDD1: ${alignr}${fs_free /media/HDD1} / ${fs_size /media/HDD1}
${fs_bar 4 /media/HDD1}
HDD2: ${alignr}${fs_free /media/HDD2} / ${fs_size /media/HDD2}
${fs_bar 4 /media/HDD2}
HDD3: ${alignr}${fs_free /media/HDD3} / ${fs_size /media/HDD3}
${fs_bar 4 /media/HDD3}

${color white}NETWORK ${hr 1}${color}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107} ${alignr}${upspeedgraph eth0 25,107}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

${color white}WEATHER ${hr 1}${color}

${execi 1800 /home/johan/Scripts/weather.sh SWXX0006}

```

---

### Post by czgirb on 2013-08-03
> **NikTh said:**
> 
As for the goutputstream... files, as @deadflowr said, is a known bug. Create a script with following contents and put it in startup applications. 
```

#!/bin/bash 
curr=.goutputstream-*
 if [[ -e /home/czgirb/$curr ]]; then
 `rm .goutputstream-*`
 exit 0
else
 exit 1
fi

``` 
Lets name it **remove-polution.sh. **Now click startup applications and add new, at command write /home/czgirb/remove-polution.sh
Give executable permissions on script 
```
chmod +x remove-polution.sh
``` 

Regards 
NikTh

Please confirm my action :
1. Open **Text Editor** and Copy-Paste **#!/bin/bash**
2. **Save** the file > name it **remove-polution.sh** > and place it in **Home** folder
3. Open **Startup Application** > **Add** new, **name: gOutPutStream** / **command: /home/czgirb/remove-polution.sh**
4. and then ... **how to give executable permissions on script ?**

SORRY ... I'm a newbie

---

### Post by deadflowr on 2013-08-03
Doing a quick copying of your .conkyrc file you posted, it ran fine for me(with the notable exceptions of the multiple media disks, which I don't have and the weather script).
Don't know what is causing it to say no configuration file, but maybe try re-installing conky.
Or better yet, install conky-all
```
sudo apt-get install conky-all
```

As for the goutputstream script, follow NikTh's command by opening up a terminal and running the chmod +x command as stated.
That will make the script itself executable.
No need to worry about the startup application needing to be marked as executable as that happened when it was created.

Another thing with conkyrc file you could try is to copy it and then rename the copy with a stupid name like number2 and then try running the config option
```
conky --config /home/username/number2
```

---

### Post by NikTh on 2013-08-04
> **czgirb said:**
> Please confirm my action :
1. Open **Text Editor** and Copy-Paste **#!/bin/bash**
2. **Save** the file > name it **remove-polution.sh** > and place it in **Home** folder
3. Open **Startup Application** > **Add** new, **name: gOutPutStream** / **command: /home/czgirb/remove-polution.sh**
4. and then ... **how to give executable permissions on script ?**

SORRY ... I'm a newbie

Not only #!/bin/bash. All the following contents. 
```

#!/bin/bash 
curr=.goutputstream-*
 if [[ -e /home/czgirb/$curr ]]; then
 `rm .goutputstream-*`
 exit 0
else
 exit 1
fi
``` 
as you see it above. Then save the document as **remove-polution.sh** 


Make it executable by executing the following command (it should return nothing)
```
chmod +x remove-polution.sh
``` 

Then follow the step 3 from above list, this is correct, and should be fine. 

As for the conky, this message 
```
Conky: **missing text block** in configuration; exiting
czgirb@czgirb:~$
``` says, that you have something wrong in TEXT  . I found that many **alignr **are without **brackets. **

Example 
```

CPU1 ${alignr}${cpu cpu1}%
${cpubar 4 cpu1}
CPU2 ${alignr}${cpu cpu2}%
${cpubar 4 cpu2}
```

Above is correct, 
```

Hostname: $[COLOR=#ff0000]alignr[/COLOR]$nodename
Kernel: $[COLOR=#ff0000]alignr[/COLOR]$kernel
Uptime: $alignr$uptime
Temp: ${alignr}${acpitemp}C
```
[s]above is wrong. **Missing brackets in alignr**[/s]** (this is not true, it can work without brackets too). **

Fix the .conkyrc file with an editor. Give in terminal 
```
gedit .conkyrc
``` 

and fix it. 

Regards
 NikTh

---

### Post by czgirb on 2013-08-05
[SIZE=4]**@deadflowr**[/SIZE]

Installed Conky-all already

conky --config /home/czgirb/ccc
*** Named **conkyrc** to **ccc**
```

czgirb@czgirb:~$ conky --config /home/czgirb/ccc
Conky: invalid configuration file '/home/czgirb/ccc'

Conky: invalid configuration file '/home/czgirb/.conkyrc'

Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_context_free();

    With the parameter:

    context

    being NULL. Please fix your program.
czgirb@czgirb:~$ 

```


[SIZE=4]**@NikTh**[/SIZE]
remove-polution.sh is OK

Regarding to the file, I re-download and revised it
```

background no
font Sans:size=8
#xftfont Sans:size=10
use_xft yes
xftalpha 0.9
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 220
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color green
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase

TEXT
${color white}SYSTEM ${hr 1}${color}

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Temp: ${alignr}${acpitemp}C

CPU: ${alignr}${freq} MHz
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

CPU1 ${alignr}${cpu cpu1}%
${cpubar 4 cpu1}
CPU2 ${alignr}${cpu cpu2}%
${cpubar 4 cpu2}

Ram ${alignr}$mem / $memmax ($memperc%)
${membar 4}
swap ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

${color white}Filesystem ${hr 1}${color}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /home}
HDD0: ${alignr}${fs_free /media/HDD0} / ${fs_size /media/HDD0}
${fs_bar 4 /media/HDD0}
HDD1: ${alignr}${fs_free /media/HDD1} / ${fs_size /media/HDD1}
${fs_bar 4 /media/HDD1}
HDD2: ${alignr}${fs_free /media/HDD2} / ${fs_size /media/HDD2}
${fs_bar 4 /media/HDD2}
HDD3: ${alignr}${fs_free /media/HDD3} / ${fs_size /media/HDD3}
${fs_bar 4 /media/HDD3}

${color white}NETWORK ${hr 1}${color}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107} ${alignr}${upspeedgraph eth0 25,107}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

${color white}WEATHER ${hr 1}${color}

${execi 1800 /home/johan/Scripts/weather.sh SWXX0006}

```

**But it still do not make my conky show up / displayed**

---

### Post by deadflowr on 2013-08-05
Unfortunately, the error message is baffling me.
Typically, and I think NikTh stated earlier, it's usually associated with missing TEXT information.
But I copied and tried your conkyrc file and it ran fine for me.

Again my suggestion at this point would be to try and reinstall the conky-all program.
```
sudo apt-get install --reinstall conky-all
```

---

### Post by stinkeye on 2013-08-05
As a test, save this config to **/home/czgirb/.conkyrc** then run **conky** in terminal.
It's your config from post #13. I just deleted your variables below "TEXT" to only display the words "This is a conky test"

Save as **.conkyrc** to home folder. (must have the preceding dot for conky to recognize)
```
background no
font Sans:size=8
#xftfont Sans:size=10
use_xft yes
xftalpha 0.9
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 220
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color green
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase

TEXT
This is a conky test
```

---

### Post by NikTh on 2013-08-05
Maybe there is a mistake here, with **weather.sh** script ? 

Try to save the following as **.conkyrc **
```

background no
font Sans:size=8
#xftfont Sans:size=10
use_xft yes
xftalpha 0.9
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 220
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color green
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase

TEXT
${color white}SYSTEM ${hr 1}${color}

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Temp: ${alignr}${acpitemp}C

CPU: ${alignr}${freq} MHz
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

CPU1 ${alignr}${cpu cpu1}%
${cpubar 4 cpu1}
CPU2 ${alignr}${cpu cpu2}%
${cpubar 4 cpu2}

Ram ${alignr}$mem / $memmax ($memperc%)
${membar 4}
swap ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

${color white}Filesystem ${hr 1}${color}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /home}
HDD0: ${alignr}${fs_free /media/HDD0} / ${fs_size /media/HDD0}
${fs_bar 4 /media/HDD0}
HDD1: ${alignr}${fs_free /media/HDD1} / ${fs_size /media/HDD1}
${fs_bar 4 /media/HDD1}
HDD2: ${alignr}${fs_free /media/HDD2} / ${fs_size /media/HDD2}
${fs_bar 4 /media/HDD2}
HDD3: ${alignr}${fs_free /media/HDD3} / ${fs_size /media/HDD3}
${fs_bar 4 /media/HDD3}

${color white}NETWORK ${hr 1}${color}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107} ${alignr}${upspeedgraph eth0 25,107}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}
```

then run ```
conky
``` from terminal and paste here the full output.

---

### Post by czgirb on 2013-09-01
> **deadflowr said:**
> Unfortunately, the error message is baffling me.
Typically, and I think NikTh stated earlier, it's usually associated with missing TEXT information.
But I copied and tried your conkyrc file and it ran fine for me.

Again my suggestion at this point would be to try and reinstall the conky-all program.
```
sudo apt-get install --reinstall conky-all
```

```

czgirb@czgirb:~$ sudo apt-get install --reinstall conky-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 9 not upgraded.
Need to get 399 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://id.archive.ubuntu.com/ubuntu/ precise/universe conky-all i386 1.8.1-6 [399 kB]
Fetched 399 kB in 5s (78.9 kB/s)                        
(Reading database ... 193165 files and directories currently installed.)
Preparing to replace conky-all 1.8.1-6 (using .../conky-all_1.8.1-6_i386.deb) ...
Unpacking replacement conky-all ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Processing triggers for menu ...
Setting up conky-all (1.8.1-6) ...
Processing triggers for menu ...
czgirb@czgirb:~$ 

```

---

### Post by czgirb on 2013-09-01
> **NikTh said:**
> 
Maybe there is a mistake here, with **weather.sh** script ? 
Try to save the following as **.conkyrc **...
*** I paste in a **new text editor**
*** Saved, and named it [B]conkyrc
[/B]*** **Cut** it and **paste** it in **home folder**
*** **Added a point in front of** conkyrc's name ... **.conkyrc**
then run ```
conky
``` from terminal and paste here the full output.


```

czgirb@czgirb:~$ conky
Conky: statfs '/media/HDD0': No such file or directory
Conky: statfs '/media/HDD1': No such file or directory
Conky: statfs '/media/HDD2': No such file or directory
Conky: statfs '/media/HDD3': No such file or directory
Conky: desktop window (1200095) is subwindow of root window (ad)
Conky: window type - normal
Conky: drawing to created window (0x3e00001)
Conky: drawing to double buffer
Conky: statfs '/media/HDD3': No such file or directory
Conky: statfs '/media/HDD2': No such file or directory
Conky: statfs '/media/HDD1': No such file or directory
Conky: statfs '/media/HDD0': No such file or directory
Conky: statfs '/media/HDD3': No such file or directory
Conky: statfs '/media/HDD2': No such file or directory
Conky: statfs '/media/HDD1': No such file or directory
Conky: statfs '/media/HDD0': No such file or directory
Conky: statfs '/media/HDD3': No such file or directory
Conky: statfs '/media/HDD2': No such file or directory
Conky: statfs '/media/HDD1': No such file or directory
Conky: statfs '/media/HDD0': No such file or directory

```

---

### Post by czgirb on 2013-09-01
[SIZE=5]**Just a suggestion only ...**[/SIZE]
How about to **remove/uninstall/delete/clean** all installed conky and have it a **new/re-install/clean/fresh** conky?
```
sudo apt-get purge --remove conky.*
```
Is the command is right?

Please help me to revise it ... if it's not. Cos I'm _a newbie to Ubuntu_ and _my computer knowledge is not sufficient enough_
All I have is _just a little ??? in order to give it Ubuntu a try_ ... and I love it

---

### Post by deadflowr on 2013-09-01
You should just have to run
```
sudo apt-get purge conky-all
```
then run an apt-get update.

But aside from that, are those media/HDDX's mounted at start up or something.
Did you add them to fstab or something.
If not, then I'd suggest commenting them out(#) until you can figure out how to get them to work.

Edit: Oh and I'd say save a copy of the .conkyrc file somewhere safe like your Documents folder.
I say this because the purge command is suppose to(doesn't mean it does) remove configuration files and I'm not sure what would happen to the conkyrc file.
Better safe than sorry.

---

### Post by ajgreeny on 2013-09-01
Don't worry about losing the current .conkyrc file as it's in your home and remove/purge commands never touch anything in there.

---

### Post by czgirb on 2013-09-04
1. sudo apt-get purge conky-all 
2. sudo apt-get update
3. Finished

But aside from that, are those media/HDDX's mounted at start up or something.
*** Do you mean an external HDD? Yes! My 500GB Seagate.

Did you add them to fstab or something.
*** Sorry ... I do not know what is FSTAB or something
*** I just a newbie. What I used is default setting.

If not, then I'd suggest commenting them out(#) until you can figure out how to get them to work.
*** What it mean? Commenting who out? **Sorry for my English**.

---

### Post by stinkeye on 2013-09-04
The application **conky** needs a config file to determine what is displayed on screen.
When running conky it looks for a config file at **~/.conkyrc**
Installing conky **DOES NOT** install a **~/.conkyrc**
If ~/.conkyrc doesn't exist it will load a very basic sample config from /etc/conky/conky.conf

So any config you download will be someone else's  config customized for their computer setup.
eg the config you are using shows info for various hard drives (HDD0 HDD1 etc) which maybe you don't have or are not mounted.
For the info from these hard drives to be shown in conky they must exist and be mounted.
To automount at boot you would add them to your **/etc/fstab** file.
**df -h** will show mounted drives.

If you don't have these drives you can edit/delete that section in the config or comment it out.
Placing a "[COLOR="#FF0000"]#[/COLOR]" symbol in front of a line stops it from being parsed by conky.
eg to comment out the mounted HDD section in the config you posted....
```
[COLOR="#FF0000"]#[/COLOR]HDD0: ${alignr}${fs_free /media/HDD0} / ${fs_size /media/HDD0}
[COLOR="#FF0000"]#[/COLOR]${fs_bar 4 /media/HDD0}
[COLOR="#FF0000"]#[/COLOR]HDD1: ${alignr}${fs_free /media/HDD1} / ${fs_size /media/HDD1}
[COLOR="#FF0000"]#[/COLOR]${fs_bar 4 /media/HDD1}
[COLOR="#FF0000"]#[/COLOR]HDD2: ${alignr}${fs_free /media/HDD2} / ${fs_size /media/HDD2}
[COLOR="#FF0000"]#[/COLOR]${fs_bar 4 /media/HDD2}
[COLOR="#FF0000"]#[/COLOR]HDD3: ${alignr}${fs_free /media/HDD3} / ${fs_size /media/HDD3}
[COLOR="#FF0000"]#[/COLOR]${fs_bar 4 /media/HDD3}
```


This huge thread exists for the showing and sharing of your conky config and general conky help....
[**_[COLOR="#B22222"]Post your .conkyrc files w/ screenshots[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=2227")

---

### Post by ajgreeny on 2013-09-04
In view of your newness to Ubuntu, I am.surprised that you have chosen conky as an application to try out; it is one of the most complicated to get working with all the things you might want to show, as you are finding.

Have a look at some example ~/.conkyrc files on the site suggested above, but don't expect them to work for you before you edit them to your own system setup, which may take some time.  I first started using conky years ago but once you start you never stop making minor edits to the configuration file to get exactly what you want, and I am still doing that nowadays.

---


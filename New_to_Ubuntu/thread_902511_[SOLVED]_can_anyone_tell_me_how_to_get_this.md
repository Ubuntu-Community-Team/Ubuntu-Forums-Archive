---
title: "[SOLVED] can anyone tell me how to get this:"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by einfinger on 2008-08-27
[http://linuxowns.files.wordpress.com/2008/08/desktop.png](http://linuxowns.files.wordpress.com/2008/08/desktop.png)

im aware that it is fluxbox and all, i have that installed. what im wondering is how i can get the text based gui thats on the right there, and remember im a total linux noob :)

thanx

---

### Post by %hMa@?b&lt;C on 2008-08-27
that looks like conky
[http://conky.sourceforge.net/](http://conky.sourceforge.net/)
should be in the repos too

---

### Post by einfinger on 2008-08-27
conky is too complex for me, i have no idea how to get it to work :/

---

### Post by %hMa@?b&lt;C on 2008-08-27
[http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/](http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/)
thats like... the exact one in your picture :P  hope the guide is helpful!

---

### Post by northern lights on 2008-08-27
> **einfinger said:**
> conky is too complex for me, i have no idea how to get it to work :/
While writing your own config file might or might not be too complex for you (don't give up too quickly!), you can definitely manage to install and run it.

Run ```
sudo apt-get update && sudo apt-get install conky
```to install and then just start it by hitting "Alt+F2" and typing 'conky'.

There's a multitude of config files downloadable on the web.

[EDIT]
> **jeffc313 said:**
> [http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/](http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/)
+1
[/EDIT]

---

### Post by einfinger on 2008-08-27
ah, great :D   one more thing tho, i cant seem to save the conf file in the directory it has to be in, im getting "you dont have permission" :(

---

### Post by northern lights on 2008-08-27
> **einfinger said:**
> ah, great :D   one more thing tho, i cant seem to save the conf file in the directory it has to be in, im getting "you dont have permission" :(
You should have permission to modify a file in your home folder.

Do you realize, that```
~/.conkyrc
```
and```
/home/USER/.conkyrc
```are the same thing? (USER needs to be replaced by your username)

I.e. If you run ```
gedit ~/.conkyrc
```you should be able to save.

---

### Post by Nythain on 2008-08-27
wich conf file... the .conckyrc should be saved in your home directory... not sure about any other scripts the user might be including (conky users usually also run a billion python scripts for further enhanceability)

---

### Post by einfinger on 2008-08-27
i got it running by just using nautilus.

ive copied the code for the conky conf file but its not showing up in my desktop..heres the code:

    background yes
    use_xft yes
    xftfont 123:size=8
    xftalpha 0.1
    update_interval 0.5
    total_run_times 0
    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 250 5
    maximum_width 400
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no
    default_color gray
    default_shade_color red
    default_outline_color green
    alignment top_right
    gap_x 10
    gap_y 10
    no_buffers no
    uppercase no
    cpu_avg_samples 2
    net_avg_samples 1
    override_utf8_locale yes
    use_spacer yes
    text_buffer_size 256

    TEXT

    ${font openlogos:size=20}U${font Arial:size=20}${color Tan1}GNU${color Ivory}LINUX${font openlogos:size=20}t

    ${voffset -90}
    ${color DimGray}
    ${font}
    ${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
    $font${color DimGray}$sysname $kernel $alignr $machine
    Intel Pentium D $alignr${freq_g cpu0}Ghz
    Uptime $alignr${uptime}
    File System $alignr${fs_type}

    ${font Arial:bold:size=10}${color Tan1}PROCESSORS ${color DarkSlateGray}${hr 2}
    $font${color DimGray}CPU1  ${cpu cpu1}% ${cpubar cpu1}
    CPU2  ${cpu cpu2}% ${cpubar cpu2}

    ${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
    $font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
    $membar

    ${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
    $font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
    ${fs_bar /home}
    /disk $alignc ${fs_used /media/disk} / ${fs_size /media/disk} $alignr ${fs_free_perc /media/disk}%
    ${fs_bar /media/disk}
    /disk-1 $alignc ${fs_used /media/disk-1} / ${fs_size /media/disk-1} $alignr ${fs_free_perc /media/disk-1}%
    ${fs_bar /media/disk-1}

    ${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
    ${color DimGray}$font${top_mem name 2}${alignr}${top mem 2} %
    $font${top_mem name 3}${alignr}${top mem 3} %
    $font${top_mem name 4}${alignr}${top mem 4} %
    $font${top_mem name 5}${alignr}${top mem 5} %

    ${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
    $font${color DimGray}IP on eth0 $alignr ${addr eth0}

    Down $alignr ${downspeed eth0} kb/s
    Up $alignr ${upspeed eth0} kb/s

    Downloaded: $alignr  ${totaldown eth0}
    Uploaded: $alignr  ${totalup eth0}

    ${font Arial:bold:size=10}${color Tan2}WEATHER ${color DarkSlateGray}${hr 2}
    ${font}${color DimGray}

    ${voffset -25}${font Weather:size=45}${execi 1800 conkyForecast –location=BEXX0008 –datatype=WF}
    ${alignc 22}${voffset -60}${font Arial:bold:size=10}${color DimGray}${execi 1800 conkyForecast –location=BEXX0008 –datatype=HT}
    $font${voffset -55}${alignr}${color DimGray}Wind: ${execi 1800 conkyForecast –location=BEXX0008 –datatype=WS}
    ${alignr}${color DimGray}Humidity: ${execi 1800 conkyForecast –location=BEXX0008 –datatype=HM}
    ${alignr}${color DimGray}Precipitation: ${execi 1800 conkyForecast –location=BEXX0008 –datatype=PC}

    ${color DimGray}Sunrise: $alignr${execi 1800 conkyForecast –location=BEXX0008 –datatype=SR}${alignr}
    Sunset: $alignr${execi 1800 conkyForecast –location=BEXX0008 –datatype=SS}$color

    ${font Arial:bold:size=10}${color Tan2}MUSIC ${color DarkSlateGray}${hr 2}
    ${color DimGray}$font${if_running mpd}
    $mpd_smart
    $mpd_album
    Bitrate $mpd_bitrate kbits/s
    $mpd_status $mpd_elapsed/$mpd_length

    ${font Arial:bold:size=10}${color Tan2}TIME ${color DarkSlateGray}${hr 2}

    ${color DarkSlateGray} ${font :size=30}$alignc${time %H:%Mh}
    ${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
    ${font :bold:size=8}$alignc${time %A}
    $endif

---

### Post by northern lights on 2008-08-27
Under 'TEXT' just put 'TEST' for now. Does that not appear?

Are you certain it's the right file in the right location?

Can you either post the ouput of ```
cat ~/.conkyrc
```or confirm that it's correct?

Further please wrap code in code tags in the future (see hash/pound button).

---

### Post by einfinger on 2008-08-27
the test text doesnt appear, and my config file is located in the examples folder in conky.

i dont know how to get the cat output :S

sorry about the code btw

---

### Post by Nythain on 2008-08-27
move your file to your home directory and name it
.conkyrc
if i remember correctly

---

### Post by einfinger on 2008-08-27
that didnt work

---

### Post by northern lights on 2008-08-27
> **einfinger said:**
> my config file is located in the examples folder in conky

```
~/.conkyrc
```is the only location from whence it will work.
It's all over this thread...

---

### Post by einfinger on 2008-08-27
im getting permission denied when i post ~/.conkyrc

---

### Post by Kevbert on 2008-08-27
Just type
```
conky
```
in terminal to run the file.

---

### Post by einfinger on 2008-08-27
if i type conky i get: Conky: missing text block in configuration; exiting

---

### Post by Kevbert on 2008-08-27
Ok, rename the .conkyrc file to conkyrc_old with
```
cp .conkyrc conkyrc_old
```
and then type conky in the terminal.  You should get the default one that comes built in.

---

### Post by BDNiner on 2008-08-27
> **einfinger said:**
> im getting permission denied when i post ~/.conkyrc

try: 
```

sudo gedit ~/.conkyrc

```

You should then be able to save the file after you make changes. Look at the ubuntu documentation site if you want to alter the permissions permanently, the command to research is "chmod".

---

### Post by northern lights on 2008-08-27
> **BDNiner said:**
> ```
sudo gedit ~/.conkyrc
```
You should then be able to save the file after you make changes. Look at the ubuntu documentation site if you want to alter the permissions permanently, the command to research is "chmod".

Please **never** run graphical applications with *sudo*. If you must launch a graphical application as superuser, use ```
gksu GRAPHICAL APP
```instead. The KDE equivalent is *kdesu*. Refer to [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo") for reference.

Further, ```
~/
```refers to the respective user's home directory. As such, once again, it is equivalent to```
/home/USER/
```i.e. it should not even be necessary to access it as root.

@ the OP:
If you run```
gedit ~/.conkyrc &
```from a terminal, what exactly happens?
(To be safe, copy/paste command into the shell)

---

### Post by BDNiner on 2008-08-27
yes it is good practice to run graphical applications using gksudo, since issues can arise when you use sudo. But gedit is not an application where that matters, firefox one the other hand would behave strangely if it was run using sudo as opposed to gksudo.

since you are getting the error "missing text block on configuration" when you run conky I would suggest that you completely remove conky and reinstall it. Mainly because if you are using the config file that was posted earlier then the TEXT section is there so there may be an issue with the installation.

```

sudo apt-get remove --purge conky
sudo apt-get install conky

```

---

### Post by billgoldberg on 2008-08-27
Did you follow part one from the guide I wrote?

--

Remove conky and install it again like another user said.

Go to "Places -> Home Folder"

Create a new file in there called ".conkyrc"

Then in a terminal run "conky".

The conky file should show up there.

It will not be exactly like the one in the picture since you won't have the weather script yet, and chances are you aren't using MPD as you music player.

The guide also tells you how to display music from exaile and rythmbox.

Also make sure you installed the openlogos font. It's all in the guide.

---

### Post by einfinger on 2008-08-28
i got it working, thanx alot :)

---


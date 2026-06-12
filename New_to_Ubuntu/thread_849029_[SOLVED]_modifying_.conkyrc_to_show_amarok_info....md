---
title: "[SOLVED] modifying .conkyrc to show amarok info..."
date: 2008-07-04
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-07-04
```
background yes
font Zekton:size=8
xftfont Zekton:size=8
use_xft yes
xftalpha 0.1
update_interval 0.6
total_run_times 0
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no
own_window_transparent yes


double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 256 5
maximum_width 300
default_color 000000
default_shade_color black
default_outline_color black
alignment top_right
gap_x 2
gap_y 27
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT
${font Zekton:style=Bold:pixelsize=24}${alignc}${time %l:%M:%S %p}${font Zekton:size=8}
SYSTEM ${hr 1 }

CPU       ${alignc} ${freq_dyn}MHz / ${acpitempf}F ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Processes: ${alignr}$processes ($running_processes running)

Highest CPU $alignr CPU%       MEM%
${top name 1}$alignr${top cpu 1}         ${top mem 1}
${top name 2}$alignr${top cpu 2}         ${top mem 2}
${top name 3}$alignr${top cpu 3}         ${top mem 3}

Load: ${alignr}$loadavg

FILESYSTEM ${hr 1}${color}

Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /}
External: ${alignr}${fs_free /media/disk} / ${fs_size /media/disk}
${fs_bar 4 /media/disk}
Flash Drive: ${alignr}${fs_free /media/disk1} / ${fs_size /media/disk1}
${fs_bar 4 /media/disk1}
NETWORK ${hr 1}${color}

Down ${downspeed wlan0} k/s ${alignr}Up ${upspeed wlan0} k/s
${downspeedgraph wlan0 24,128} ${alignr}${upspeedgraph wlan0 24,128}
Total ${totaldown wlan0} ${alignr}Total ${totalup wlan0}

MUSIC ${hr 1}${color}

${color}${alignc}Now Playing${color black}
${alignc}${execi 10 ~/.conkyamarok artist}
${alignc}${execi 10 ~/.conkyamarok title}
${execibar 1 ~/.conkyamarok progress}
${alignc}"${execi 10 ~/.conkyamarok album}"
${alignc}${execi 10 ~/.conkyamarok year} - ${color black}${alignc}${execi 10 ~/.conkyamarok genre}
$color$stippled_hr
${alignc}Collection Information
Artists: ${color black}${execi 10 ~/.conkyamarok totalArtists} $color${alignr}Compilations: ${color black}${execi 10 ~/.conkyamarok totalCompilations}$color
Albums:  ${color black}${execi 10 ~/.conkyamarok totalAlbums} $color${alignr}Genres: ${color black}${execi 10 ~/.conkyamarok totalGenres}$color
Tracks:  ${color black}${execi 10 ~/.conkyamarok totalTracks}
$color$stippled_hr
}${color})$endif


```
my .conkyrc

```
#!/bin/bash
# amaroK info display script by eirc <eirc.eirc@gmail.com>
#
# requirements: amaroK (!)
# for Collection stats to work amarok must be using
# mySQL to store it's collection

case "$1" in

# Now Playing Info
artist) dcop amarok player artist ;;
title)  dcop amarok player title ;;
album)  dcop amarok player album ;;
year)   dcop amarok player year ;;
genre)  dcop amarok player genre ;;
progress)
    curr=`dcop amarok player trackCurrentTime`
    tot=`dcop amarok player trackTotalTime`
    if (( $tot )); then
        expr $curr \* 100  / $tot
    fi
    ;;

# Collection Info
totalArtists)      dcop amarok collection totalArtists ;;
totalAlbums)       dcop amarok collection totalAlbums ;;
totalTracks)       dcop amarok collection totalTracks ;;
totalGenres)       dcop amarok collection totalGenres ;;
totalCompilations) dcop amarok collection totalCompilations ;;

# Collection Stats
most_songs_by_artist) dcop amarok collection query 'SELECT t1.name FROM artist t1 INNER JOIN tags t2 ON t1.id = t2.artist GROUP BY t2.artist ORDER BY COUNT(t2.artist) DESC LIMIT 1;' ;;
most_songs_by_artist_n) dcop amarok collection query 'SELECT count(t2.artist) FROM artist t1 INNER JOIN tags t2 ON t1.id = t2.artist GROUP BY t2.artist ORDER BY COUNT(t2.artist) DESC LIMIT 1;' ;;
most_songs_are_genre) dcop amarok collection query 'SELECT t1.name FROM genre t1 INNER JOIN tags t2 ON t1.id = t2.genre GROUP BY t2.genre ORDER BY COUNT(t2.genre) DESC LIMIT 1;' ;;
most_songs_are_genre_n) dcop amarok collection query 'SELECT count(t2.genre) FROM genre t1 INNER JOIN tags t2 ON t1.id = t2.genre GROUP BY t2.genre ORDER BY COUNT(t2.genre) DESC LIMIT 1;' ;;
most_songs_during_year) dcop amarok collection query 'SELECT t1.name FROM year t1 INNER JOIN tags t2 ON t1.id = t2.year GROUP BY t2.year ORDER BY COUNT(t2.year) DESC LIMIT 1;' ;;
most_songs_during_year_n) dcop amarok collection query 'SELECT count(t2.year) FROM year t1 INNER JOIN tags t2 ON t1.id = t2.year GROUP BY t2.year ORDER BY COUNT(t2.year) DESC LIMIT 1;' ;;
most_albums_by_artist) dcop amarok collection query 'SELECT name FROM artist WHERE id=(SELECT t1.artist from (SELECT artist FROM tags GROUP BY album) AS t1 GROUP BY t1.artist ORDER BY count(artist) DESC LIMIT 1);' ;;
most_albums_by_artist_n) dcop amarok collection query 'SELECT count(artist) from (SELECT artist FROM tags GROUP BY album) AS t1 GROUP BY t1.artist ORDER BY count(artist) DESC LIMIT 1;' ;;
most_albums_are_genre) dcop amarok collection query 'SELECT name FROM genre WHERE id=(SELECT t1.genre from (SELECT genre FROM tags GROUP BY album) AS t1 GROUP BY t1.genre ORDER BY count(genre) DESC LIMIT 1);' ;;
most_albums_are_genre_n) dcop amarok collection query 'SELECT count(genre) from (SELECT genre FROM tags GROUP BY album) AS t1 GROUP BY t1.genre ORDER BY count(genre) DESC LIMIT 1;' ;;
most_albums_during_year) dcop amarok collection query 'SELECT name FROM year WHERE id=(SELECT t1.year from (SELECT year FROM tags GROUP BY album) AS t1 GROUP BY t1.year ORDER BY count(year) DESC LIMIT 1);' ;;
most_albums_during_year_n) dcop amarok collection query 'SELECT count(year) from (SELECT year FROM tags GROUP BY album) AS t1 GROUP BY t1.year ORDER BY count(year) DESC LIMIT 1;' ;;

esac


```
my .conkyamarok file

im trying to get it to work im using a user name of root and have mysql configured and my amarok running off of it, anyone have any idea of what im missing?

---

### Post by PatrickMoore on 2008-07-04
i changed back to what conky reccomended...
```
background yes
font Zekton:size=8
xftfont Zekton:size=8
use_xft yes
xftalpha 0.1
update_interval 0.6
total_run_times 0
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no
own_window_transparent yes


double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 256 5
maximum_width 300
default_color 000000
default_shade_color black
default_outline_color black
alignment top_right
gap_x 2
gap_y 27
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT
${font Zekton:style=Bold:pixelsize=24}${alignc}${time %l:%M:%S %p}${font Zekton:size=8}
SYSTEM ${hr 1 }

CPU       ${alignc} ${freq_dyn}MHz / ${acpitempf}F ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Processes: ${alignr}$processes ($running_processes running)

Highest CPU $alignr CPU%       MEM%
${top name 1}$alignr${top cpu 1}         ${top mem 1}
${top name 2}$alignr${top cpu 2}         ${top mem 2}
${top name 3}$alignr${top cpu 3}         ${top mem 3}

Load: ${alignr}$loadavg

FILESYSTEM ${hr 1}${color}

Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /}
External: ${alignr}${fs_free /media/disk} / ${fs_size /media/disk}
${fs_bar 4 /media/disk}
Flash Drive: ${alignr}${fs_free /media/disk1} / ${fs_size /media/disk1}
${fs_bar 4 /media/disk1}
NETWORK ${hr 1}${color}

Down ${downspeed wlan0} k/s ${alignr}Up ${upspeed wlan0} k/s
${downspeedgraph wlan0 24,128} ${alignr}${upspeedgraph wlan0 24,128}
Total ${totaldown wlan0} ${alignr}Total ${totalup wlan0}

MUSIC ${hr 1}${color}

$color$stippled_hr${if_running amarokapp}
${color}${alignc}Now Playing${color black}
${alignc}${execi 10 ~/.conky/amarok artist}
${alignc}${execi 10 ~/.conky/amarok title}
${execibar 1 ~/.conky/amarok progress}
${alignc}"${execi 10 ~/.conky/amarok album}"
${alignc}${execi 10 ~/.conky/amarok year} - ${color white}${alignc}${execi 10 ~/.conky/amarok genre}
$color$stippled_hr
${alignc}Collection Information
Artists: ${color white}${execi 10 ~/.conky/amarok totalArtists} $color${alignr}Compilations: ${color white}${execi 10 ~/.conky/amarok totalCompilations}$color
Albums:  ${color white}${execi 10 ~/.conky/amarok totalAlbums} $color${alignr}Genres: ${color white}${execi 10 ~/.conky/amarok totalGenres}$color
Tracks:  ${color white}${execi 10 ~/.conky/amarok totalTracks}
$color$stippled_hr
}${color})$endif


```

```
#!/bin/bash
# amaroK info display script by eirc <eirc.eirc@gmail.com>
#
# requirements: amaroK (!)
# for Collection stats to work amarok must be using
# mySQL to store it's collection

case "$1" in

# Now Playing Info
artist) dcop amarok player artist ;;
title)  dcop amarok player title ;;
album)  dcop amarok player album ;;
year)   dcop amarok player year ;;
genre)  dcop amarok player genre ;;
progress)
    curr=`dcop amarok player trackCurrentTime`
    tot=`dcop amarok player trackTotalTime`
    if (( $tot )); then
        expr $curr \* 100  / $tot
    fi
    ;;

# Collection Info
totalArtists)      dcop amarok collection totalArtists ;;
totalAlbums)       dcop amarok collection totalAlbums ;;
totalTracks)       dcop amarok collection totalTracks ;;
totalGenres)       dcop amarok collection totalGenres ;;
totalCompilations) dcop amarok collection totalCompilations ;;

# Collection Stats
most_songs_by_artist) dcop amarok collection query 'SELECT t1.name FROM artist t1 INNER JOIN tags t2 ON t1.id = t2.artist GROUP BY t2.artist ORDER BY COUNT(t2.artist) DESC LIMIT 1;' ;;
most_songs_by_artist_n) dcop amarok collection query 'SELECT count(t2.artist) FROM artist t1 INNER JOIN tags t2 ON t1.id = t2.artist GROUP BY t2.artist ORDER BY COUNT(t2.artist) DESC LIMIT 1;' ;;
most_songs_are_genre) dcop amarok collection query 'SELECT t1.name FROM genre t1 INNER JOIN tags t2 ON t1.id = t2.genre GROUP BY t2.genre ORDER BY COUNT(t2.genre) DESC LIMIT 1;' ;;
most_songs_are_genre_n) dcop amarok collection query 'SELECT count(t2.genre) FROM genre t1 INNER JOIN tags t2 ON t1.id = t2.genre GROUP BY t2.genre ORDER BY COUNT(t2.genre) DESC LIMIT 1;' ;;
most_songs_during_year) dcop amarok collection query 'SELECT t1.name FROM year t1 INNER JOIN tags t2 ON t1.id = t2.year GROUP BY t2.year ORDER BY COUNT(t2.year) DESC LIMIT 1;' ;;
most_songs_during_year_n) dcop amarok collection query 'SELECT count(t2.year) FROM year t1 INNER JOIN tags t2 ON t1.id = t2.year GROUP BY t2.year ORDER BY COUNT(t2.year) DESC LIMIT 1;' ;;
most_albums_by_artist) dcop amarok collection query 'SELECT name FROM artist WHERE id=(SELECT t1.artist from (SELECT artist FROM tags GROUP BY album) AS t1 GROUP BY t1.artist ORDER BY count(artist) DESC LIMIT 1);' ;;
most_albums_by_artist_n) dcop amarok collection query 'SELECT count(artist) from (SELECT artist FROM tags GROUP BY album) AS t1 GROUP BY t1.artist ORDER BY count(artist) DESC LIMIT 1;' ;;
most_albums_are_genre) dcop amarok collection query 'SELECT name FROM genre WHERE id=(SELECT t1.genre from (SELECT genre FROM tags GROUP BY album) AS t1 GROUP BY t1.genre ORDER BY count(genre) DESC LIMIT 1);' ;;
most_albums_are_genre_n) dcop amarok collection query 'SELECT count(genre) from (SELECT genre FROM tags GROUP BY album) AS t1 GROUP BY t1.genre ORDER BY count(genre) DESC LIMIT 1;' ;;
most_albums_during_year) dcop amarok collection query 'SELECT name FROM year WHERE id=(SELECT t1.year from (SELECT year FROM tags GROUP BY album) AS t1 GROUP BY t1.year ORDER BY count(year) DESC LIMIT 1);' ;;
most_albums_during_year_n) dcop amarok collection query 'SELECT count(year) from (SELECT year FROM tags GROUP BY album) AS t1 GROUP BY t1.year ORDER BY count(year) DESC LIMIT 1;' ;;

esac


```

---

### Post by PatrickMoore on 2008-07-04
I'm getting this error message wjem i start conky

sh: /home/patrick/.conky/amarok: Permission denied

---

### Post by finer recliner on 2008-07-04
i dont remember where i found this script, but here is my amarok-bash script that is called from conky:

```

#!/bin/bash
# amaroK info display script by eirc <eirc.eirc@gmail.com>
#
# requirements: amaroK (!)
# for Collection stats to work amarok must be using
# mySQL to store it's collection

case "$1" in

# Now Playing Info
artist) dcop amarok player artist ;;
title)  dcop amarok player title ;;
album)  dcop amarok player album ;;
year)   dcop amarok player year ;;
genre)  dcop amarok player genre ;;
progress)
    curr=`dcop amarok player trackCurrentTime`
    tot=`dcop amarok player trackTotalTime`
    if (( $tot )); then
        expr $curr \* 100  / $tot
    fi
    ;;
esac

```


and the relevant part of my .conkyrc:

```
${if_running amarokapp}
${color orange}Amarok | Now Playing ${hr 2}$color
${exec ~/.conky/amarok artist | fold -w50}
${exec ~/.conky/amarok title | fold -w50}
${exec ~/.conky/amarok album |fold -w50}
${execibar 1 ~/.conky/amarok progress}
$endif


```

hope it helps you

---

### Post by PatrickMoore on 2008-07-04
> **finer recliner said:**
> i dont remember where i found this script, but here is my amarok-bash script that is called from conky:

```

#!/bin/bash
# amaroK info display script by eirc <eirc.eirc@gmail.com>
#
# requirements: amaroK (!)
# for Collection stats to work amarok must be using
# mySQL to store it's collection

case "$1" in

# Now Playing Info
artist) dcop amarok player artist ;;
title)  dcop amarok player title ;;
album)  dcop amarok player album ;;
year)   dcop amarok player year ;;
genre)  dcop amarok player genre ;;
progress)
    curr=`dcop amarok player trackCurrentTime`
    tot=`dcop amarok player trackTotalTime`
    if (( $tot )); then
        expr $curr \* 100  / $tot
    fi
    ;;
esac

```


and the relevant part of my .conkyrc:

```
${if_running amarokapp}
${color orange}Amarok | Now Playing ${hr 2}$color
${exec ~/.conky/amarok artist | fold -w50}
${exec ~/.conky/amarok title | fold -w50}
${exec ~/.conky/amarok album |fold -w50}
${execibar 1 ~/.conky/amarok progress}
$endif


```

hope it helps you

i was hoping to get my script to work but i will try this one. thanks. anyone know why im getting this error?

---

### Post by PatrickMoore on 2008-07-04
im still getting this error message...

sh: /home/patrick/.conky/amarok: Permission denied

---

### Post by nowshining on 2008-07-04
do the following:

```
sudo chown -R patrick:patrick /home/patrick/
```

ur pw won't show as you type....

I suggest setting up an alias such as me and root.

ex:

me /home/patrick/

^That changes all files in ur home to have my permissions - urs in ur case

root /hom/patrick/

^changes all files to have root privs in ur home folder.

:) in ur alieas add sudo tho in front. :D so that way u'll be able to just insert ur pw after u hit the command without putting sudo first.

---

### Post by PatrickMoore on 2008-07-04
i have it up perfect now...


if anoyone wants my conkyrc let me know...

---

### Post by trump1 on 2009-05-28
Pleace can you give me your conky Patrick :)

---


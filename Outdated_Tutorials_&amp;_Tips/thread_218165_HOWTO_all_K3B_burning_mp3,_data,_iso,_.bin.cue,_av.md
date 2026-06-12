---
title: "HOWTO: all K3B burning: mp3, data, iso, .bin/.cue, avi to dvd, etc."
date: 2006-07-18
forum: Outdated Tutorials &amp; Tips
---

### Post by dr.drake on 2006-07-18
hello,

this must be the ...th thread on K3B, but the reason why I start this now, is because a lot of threads have "solutions" in the first post that don't work (anymore) or are too hard to follow. usually a better/simpler solution comes up later in the thread, but doesn't appear in the first post, so a lot of people end up doing the wrong/difficult thing first.

this is a collection of all the last options I found in various K3B threads, and I will try to update this as long as I can, adding the info from newer posts into this first one. oh, and I am using Kubuntu Dapper.
[COLOR="Red"][B][SIZE="2"]
 - latest update: juli 18th 2006 -[/SIZE][/B][/COLOR]

[COLOR="Blue"]**K3B pt 1: getting K3B**[/COLOR]

this can easily be done through your package manager (Adept, Synaptic),
if you need [repositories]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories"), check: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)


[COLOR="Blue"]**K3B pt 2: burning DATA**[/COLOR]
[LIST]
[*]just select '**New Data CD/DVD Project**' from the first menu.
[*]drag files to window, click the "**Burn**" button.
for exact copies of all the files, go to the advanced tab and mark:[LIST]
[*]**allow 103 character Joliet filenames**
[*]**allow untranslated ISO9660 filenames**[/LIST]
(if you don't do this, K3B will shorten filenames)
[*]click '**Burn**'.[/LIST]

[COLOR="Blue"]**K3B pt 3: burning MP3's**[/COLOR]

because MP3 is not a free format, it's not supported by default, and you need to install the **libk3b2-mp3** package with your package manager.

after you installed libk3b2-mp3 just:
[LIST]
[*]open K3B
[*]select '**New Audio CD Project**'
[*]drag files
[*]click '**Burn**'[/LIST]

[COLOR="Blue"]**K3B pt 4: Normalizing audio levels.**[/COLOR]

to burn a CD where the audio levels are all the same, follow [this guide]("http://www.ubuntuforums.org/showthread.php?t=30763&highlight=normalize-audio+K3B"):
> For some reason Ubuntu's repositories contain a "normalize-audio" package instead of just "normalize", and the binary is even called "normalize-audio" (even though "man normalize-audio" returns a description of the "normalize" command), so you have to create a symbolic link called "normalize" for K3B to find it properly:
```
sudo apt-get install normalize-audio
cd /usr/bin
sudo ln -s normalize-audio normalize
```
Then run K3B, 
select Settings-Configure K3b..., 
click "Programs" on the left, and click the "Search" button.
"/usr/bin/normalize" should show up under the "normalize" heading. 
**Now just make sure you turn off "On the fly" in the options for burning**, and it will let you select "Normalize volume levels" on the Advanced tab.

[COLOR="Blue"]**K3B pt 5: burning ISO files:**[/COLOR]
[LIST]
[*]open K3B
[*]select '**Burn DVD ISO image**'
[*]drag files
[*]click '**Burn**'[/LIST]

[COLOR="Blue"]**K3B pt 6: burning movies (.bin/.cue files)**[/COLOR]:
[LIST]
[*]open K3B
[*]under File > New Project select: '**New Video DVD Project**'
[*]drag the **.cue** file into the **VIDEO_TS** folder (.bin will follow automatically)
[*]drag the **audio** file (if present) into the **AUDIO_TS** folder
[*]click '**Burn**'[/LIST]
[COLOR="Blue"]
**K3B pt 7: burning movies (mpeg, avi, etc as DVD files)**[/COLOR]

now this is a tricky one...
there is a long tutorial [here]("http://www.ubuntuforums.org/showthread.php?t=183936")  that will let you convert things through the command line.
the easier option appears to be (I haven't tried this one yet) to use **[DeVeDe]("http://www.rastersoft.com/programas/devede.html")**:

first you need to install '**python-glade2**', '**mencoder**', '**dvdauthor**' and '**vcdimager**' with your package manager...
> 
[DeVeDe]("http://www.rastersoft.com/programas/devede.html") [...] has the same outcome but with much less effort. All you have to do is download the tar.bz2 file from the link at the bottom of the web site, extract it to your main folder (/home/username),

in a terminal cd to it with a:
```
cd devede
```
and then do a:
```
sudo ./install.sh
```

I'm running Dapper and this worked perfect the first time for me. It installed the desktop link in application>sound & video>devede.

The gui could'nt be easier, it does all the encoding and makes the .iso for you and it also deletes those temp files or leaves them if you prefer.

I read someone was having problems with the old conversions ending up on his newest project with tovid, thats because you're leaving the old files in your output dir. Delete those and your temp files before you start a new project that should fix it.

I had a 1hr41min encode time for a 2hr12min movie form .avi to dvd.iso, I'm not sure I have a reason to ever boot up windows xp again. I believe this was my last hurdle but I'll have to wait and see..

One last thing it told me I was using 115% of the dvd-r but I ran it anyway and the dvd.iso only ended up being 1.9gigs i believe thats thanks to mkisofs. So pay that disk usage bar nomind however it did need 11gigs of free space to acomplish this so be sure you have plenty of free space. And as mentioned before it will remove those extra tmp files that it makes.


that's it for now,

I hope I don't need to add much more in this first post, having it as complete and compact as possible..

---

### Post by k420 on 2006-07-18
hey good idea on that just discovered DeVeDe on gnomefiles but there website is down could you compile a .deb file for it or at least the attach the source file

---

### Post by dr.drake on 2006-07-19
as far as i know their site seems to be up, so you could download it there. wouldn't know how to compile a .deb file (see my sig), so can't help you there, maybe somebody else can?

---

### Post by IrishGangsta on 2006-07-29
I have DeVeDe up and running
But to me it seems it will only make a data dvd.

Can anyone give me instruction on how to burn a movie i downloaded...Not Pirated! I want to burn it to a blank DVD!

---

### Post by dr.drake on 2007-04-04
*bumped, because I see people ask these questions in new threads...

---

### Post by EminoX on 2007-07-23
*Bump*

And Thanks :KS

---

### Post by stinger30au on 2007-07-28
WOW!! awesome info.
you answered all my questions i was going to ask... but  i searched before i asked.

thanks so much

---

### Post by robertmf on 2007-08-06
Note that mencoder is broken in Fiesty.    The DeVeDe homepage at the bottom has the mencode v. Edgy

---

### Post by ponchuk on 2007-09-05
read instructions. the problem is devede.  From what i've beeenreading it does not work well. I am looking for something else like devede to convert avi to an iso so I can burn. tried devede and made iso and burned with "baker". sound problems as noted in forum. Is there a solution? I thought k3b will decode and burn the avi files.  thanks for the help

---

### Post by coolboarderguy on 2007-10-29
Hi All,

cannot see any option in K3B, where one can create an ISO from a DVD. Is it possible? BTW, good thread, thanx.

---

### Post by williambertram on 2008-05-29
libk3b2-mp3 appears to have been replaced by libk3b2-extracodecs.  Looks like it includes mp3 + more codecs.

To install:
sudo apt-get install libk3b2-extracodecs

It will inform you of this if you attempt to install -mp3 package, but thought I would post it anyway.

---

### Post by penguiniator on 2009-04-13
Here is a script that will assist in converting .avi files to DVD ISO images. It is based on documentation at [http://www.mepis.org/docs/en/index.php/AVI_to_DVD_MPEG_Conversion](http://www.mepis.org/docs/en/index.php/AVI_to_DVD_MPEG_Conversion):

#/bin/bash -

error() {
	printf '%s: %s\n' ${0##*/} "$@"
} >&2

cleanup() {
	if [[ $# -gt 1 ]]; then
		[[ -f ${2%.*}.m2v ]] && rm ${2%.*}.m2v
		[[ -f ${2%.*}.ac3 ]] && rm ${2%.*}.ac3
		[[ -f ${2%.*}.mpg ]] && rm ${2%.*}.mpg
		[[ -f ${2%.*}.xml ]] && rm ${2%.*}.xml
		[[ -d ${2%.*} ]] && rm -Rf ${2%.*}
	fi
	exit $1
}

ERROR=NO
if ! which transcode >/dev/null; then
	error "transcode must be installed to use this program"
	ERROR=YES
fi
if ! which mplex >/dev/null; then
	error "mplex must be installed to use this program"
	ERROR=YES
fi
if ! which dvdauthor >/dev/null; then
	error "dvdauthor must be installed to use this program"
	ERROR=YES
fi
if ! which mkisofs >/dev/null; then
	error "mkisofs must be installed to use this program"
	ERROR=YES
fi
if [[ $ERROR == YES ]]; then
	cleanup 1
fi
if [[ $# -lt 1 ]]; then
	error "You forgot to tell what .avi file to convert"
	cleanup 1
fi
transcode -i $1 -y ffmpeg --export_prof dvd-ntsc --export_asr 3 -o ${1%.*} -D0 -s2 -m ${1%.*}.ac3 -J modfps --export_fps 29.97 2>/dev/null &&
mplex -f8 ${1%.*}.ac3 ${1%.*}.m2v -o ${1%.*}.mpg 2>/dev/null &&
cat >${1%.*}.xml <<EOF
<dvdauthor dest="${1%.*}">
<vmgm />
<titleset>
<titles>
<pgc>
<vob file="${1%.*}.mpg" chapters="0,0:30,1:00,1:30,2:30,3:00,3:30,4:00"/>
</pgc>
</titles>
</titleset>
</dvdauthor>
EOF

if [[ -f ${1%.*}.xml ]]; then
	dvdauthor -x ${1%.*}.xml 2>/dev/null &&
	mkisofs -dvd-video -udf -o ${1%.*}.iso ${1%.*}/ 2>/dev/null
fi

cleanup 0 ${1%.*}

---


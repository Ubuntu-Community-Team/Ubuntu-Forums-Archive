---
title: "No sound with Realtek ALC883"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by feralimp on 2008-06-21
Hi everyone,

I can't get any sound with my realtek alc883 onboard sound card. I tried adding> options snd-hda-intel model=auto (as well as model=6stack-dig) to my /etc/modprobe.d/alsa-base file but with no luck. I made made sure I unmuted everything in alsamixer as well. I've seen that many people have this card working on the forum, but it isn't working for me. Any ideas?

Thanks!

---

### Post by Dizzle7677 on 2008-06-21
> **feralimp said:**
> Hi everyone,

I can't get any sound with my realtek alc883 onboard sound card. I tried adding (as well as model=6stack-dig) to my /etc/modprobe.d/alsa-base file but with no luck. I made made sure I unmuted everything in alsamixer as well. I've seen that many people have this card working on the forum, but it isn't working for me. Any ideas?

Thanks!

Use the realtek drivers for Linux@ [http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false ]("http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false")
 
It's a fairly simple install. You might need to install some lib-dev's but it'll tell you which one if it errors out. Mine worked fine from first boot even without the realtek drivers. Have you never gotten any sound at all or did it just stop working?

---

### Post by feralimp on 2008-06-21
Hi Dizzle7677,

> Have you never gotten any sound at all or did it just stop working?

Nope, never had sound.

Thanks for the link. I downloaded and compiled the driver, but I'm stuck at "step 4":
> Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
	 
        snd-xxxx is the card ID.

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel
           --- ATI chipset -----
	       snd-atiixp

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
	       snd-via82xx
           --- ATI Chipset  -------------------------------
	       snd-atiixp


There doesn't seem to be a modules.conf or conf.modules in Ubuntu.

---

### Post by Dizzle7677 on 2008-06-21
> **feralimp said:**
> 
Nope, never had sound.

  Have you tried going into Add/Remove and installing Device Manager to see your hardware layout? There could be an IRQ conflict somewhere or maybe for the simple fact it's not enabled in the BIOS(just looking at the obvious).
> **feralimp said:**
> 
Thanks for the link. I downloaded and compiled the driver, but I'm stuck at "step 4":


There doesn't seem to be a modules.conf or conf.modules in Ubuntu.[/QUOTE]

  No need to compile it despite what the readme says. Extract the file to it's directory ~ realtek-linux-audiopack-5.04 ~ and run sudo ./install from it.

---

### Post by feralimp on 2008-06-22
I tried running sudo ./install inside the extracted folder and got this at the end of the compile:

> make[1]: Leaving directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/alsactl'
Making all in alsaconf
make[1]: Entering directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/alsaconf'
Making all in po
make[2]: Entering directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/alsaconf'
make: *** [all-recursive] Error 1
Making install in include
make[1]: Entering directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/include'
make[2]: Entering directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/include'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/include'
make[1]: Leaving directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/include'
Making install in alsactl
make[1]: Entering directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/alsactl'
make[2]: Entering directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/alsactl'
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
make[2]: Leaving directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/alsactl'
make[1]: Leaving directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/alsactl'
Making install in alsaconf
make[1]: Entering directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/alsaconf'
Making install in po
make[2]: Entering directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/alsaconf/po'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/sean/Desktop/realtek-linux-audiopack-5.04/alsa-utils-1.0.16/alsaconf'
make: *** [install-recursive] Error 1
Remove Folder.....
./install: 101: alsaconf: not found


How can I tell what dependencies I need?

---

### Post by Dizzle7677 on 2008-06-22
> **feralimp said:**
> I tried running sudo ./install inside the extracted folder and got this at the end of the compile:



How can I tell what dependencies I need?

alsaconf aka alsa configuration. you can always do a search for references to 'alsa conf' or 'alsa configuration' that's applicable to your setup in the online repositories or synaptic. what you would be looking for is the main files.

alsamixergui,alsa-tools,alsa-tools-gui,alsa-utils,alsa base,alsa-oss,libasound2,libasound2-dev(<-maybe)
make sure you have these packages installed.

---

### Post by hacker_at_linux on 2009-05-26
> **Dizzle7677 said:**
> Use the realtek drivers for Linux@ [http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false ]("http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false")
 
It's a fairly simple install. You might need to install some lib-dev's but it'll tell you which one if it errors out. Mine worked fine from first boot even without the realtek drivers. Have you never gotten any sound at all or did it just stop working?

But man this one is giving an error alsaconf not found.
What is that n how to get it

---


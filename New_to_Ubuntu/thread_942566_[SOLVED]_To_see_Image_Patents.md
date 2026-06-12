---
title: "[SOLVED] To see Image Patents"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by BSG Fan on 2008-10-09
Hi again
I need to work with the patents from the USPTO but I can not see any image.

Example: 
[COLOR="Red"]http://patimg1.uspto.gov/.piw?Docid=07430527&homeurl=http%3A%2F%2Fpatft.uspto.gov%2Fnetacgi%2Fnph-Parser%3FSect1%3DPTO2%2526Sect2%3DHITOFF%2526u%3D%25252Fnetahtml%25252FPTO%25252Fsearch-adv.htm%2526r%3D45%2526p%3D1%2526f%3DG%2526l%3D50%2526d%3DPTXT%2526S1%3Dship%2526OS%3Dship%2526RS%3Dship&PageNum=&Rtype=&SectionNum=&idkey=NONE&Input=View+first+page[/COLOR]

The only they say is that I must get a download plugin but it does not find anything, 
I click a link that take me to "https://addons.mozilla.org/en-US/firefox/browse/type:7" and there is a big list of software but I go to 
"Linux Version 10" and there is 
the "**RealPlayer 11 for Linux**" (from [http://www.real.com/linux](http://www.real.com/linux))
I click it to download (it is a BIN File) 
my Laund Application tell me that the link need to be opened with an application (my pc does not suggest any)

How I open it?
What application I have to use?

Help

BDS Fan
;)

Note:
I am posting here links from other sites.  I do not know if the forum allow it, so I am asking if it is okay.  Why?  Because in the past other forums do not allow it.

---

### Post by oldos2er on 2008-10-09
[http://www.associatedcontent.com/article/705055/how_to_install_realplayer_11_in_ubuntu.html](http://www.associatedcontent.com/article/705055/how_to_install_realplayer_11_in_ubuntu.html)

---

### Post by hyper_ch on 2008-10-09
I might be wrong but isn't RealPlayer in the Canonical Partner repos? I know it was back in feisty.

---

### Post by BSG Fan on 2008-10-09
I followed the instructions but I could not download it
Sorry, confused
thanks for the help

---

### Post by ahsile on 2008-10-09
You do not need realplayer, all you need is a TIFF plugin for firefox.

This one should do the trick I hope!

[http://downloads.sourceforge.net/tiff-plugin/mozilla-tiff-plugin-0.3.2_i386.deb?modtime=1206626519&big_mirror=0](http://downloads.sourceforge.net/tiff-plugin/mozilla-tiff-plugin-0.3.2_i386.deb?modtime=1206626519&big_mirror=0)

---

### Post by BSG Fan on 2008-10-09
> **ahsile said:**
> You do not need realplayer, all you need is a TIFF plugin for firefox.

This one should do the trick I hope!

[http://downloads.sourceforge.net/tiff-plugin/mozilla-tiff-plugin-0.3.2_i386.deb?modtime=1206626519&big_mirror=0](http://downloads.sourceforge.net/tiff-plugin/mozilla-tiff-plugin-0.3.2_i386.deb?modtime=1206626519&big_mirror=0)

I downloaded it
but the images of the page does not open in TIFF images.

Yes, you are right: I need a tiff-plugin but this ome did not work with my firefoz mozila 3.0.3 Ubuntu Hardy 8

any new idea will be welcome
Thanks for ur help
;)

---

### Post by ahsile on 2008-10-09
Apparently the version linked from the sourceforge page is old, and the newer version requires manual compiling. I'll keep looking to see if there is a better alternative.

---

### Post by ahsile on 2008-10-09
Ok, was able to dig up some help in [this thread]("http://ubuntuforums.org/showthread.php?t=810107").

> 
With tiff-plugin, I was able to make use of the .deb package hosted at [http://tiff-plugin.sf.net/](http://tiff-plugin.sf.net/) using the following commands:

cd /usr/lib/xulrunner-addons/plugins/
sudo ln -s /usr/lib/firefox/plugins/mozilla-tiff-plugin.so libtiff-plugin.so


[edit]

I should note I just tested this remotely at home and I was able to view the tiff images in a randomly selected patent application...

---

### Post by oldos2er on 2008-10-09
I see you've gotten other advice, but if you still want to download Realplayer, go to [http://www.real.com/linux/](http://www.real.com/linux/)

---

### Post by LowSky on 2008-10-09
OK I'm angry!!!

When I was a noob a couple years back getting Realplayer installed was so hard. NOW...Now they have a .deb file, where was this 2 years ago!!!
[http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb](http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb)

---

### Post by BSG Fan on 2008-10-09
> **oldos2er said:**
> I see you've gotten other advice, but if you still want to download Realplayer, go to [http://www.real.com/linux/](http://www.real.com/linux/)

Hello, I am also following your advise.  This is a little complicated for me, hehe.  I appreciate ur help.
still I am in the abyss but I won't surrender

=)

---

### Post by BSG Fan on 2008-10-09
> **ahsile said:**
> Ok, was able to dig up some help in [this thread]("http://ubuntuforums.org/showthread.php?t=810107").



[edit]

I should note I just tested this remotely at home and I was able to view the tiff images in a randomly selected patent application...

--------
Thanks again!

okay, I did it but the terminal is requesting me information I unknown.
Maybe u can help me

This is the inform that I copied: But what is next?

[COLOR="Yellow"]bsgfan-desktop:~$ cd /usr/lib/xulrunner-addons/plugins/
bsgfan-desktop:/usr/lib/xulrunner-addons/plugins$ sudo ln -s /usr/lib/firefox/plugins/mozilla-tiff-plugin.so libtiff-plugin.so 
[sudo] password for bsgfan: *********
bsgfan-desktop:/usr/lib/xulrunner-addons/plugins$ [/COLOR]

So, what is next to type (or paste) there?
We are almost there...

=)

---

### Post by ahsile on 2008-10-09
I think that's it :) Just reload firefox!

---

### Post by BSG Fan on 2008-10-09
> **ahsile said:**
> I think that's it :) Just reload firefox!

You are my heroe!
Yep, I succeed thanks to you

Thanks also to every Ubuntu friend that reply to my help!
Thanks so much , people
:guitar::guitar:
:popcorn:

---


---
title: "How to fix &quot;DVD movie won't play.&quot;"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by jps2012 on 2012-04-12
That's the gist of it. Movie DVDs won't play on my Ubuntu 11.10 system (there's another thread that addresses the issue, but the post was titled "DVD," which doesn't say much about what the problem is). 

I've installed the restricted extras. I have the VLC player, and Totem. I've taken a look at the advice listed below (from another thread) and have a question about it (first I should note that most of the files listed as recommended downloads come bundled in a package--I believe--and don't need to be downloaded individually). 

Here's the previously listed (from another thread) advice: 

[B]From the Ubuntu Software Center get and install:

gst-plugins-base[/B] [B]

gstreamer0.10-plugins-good[/B] [B]

gstreamer0.10-plugins-ugly[/B] [B]

gstreamer0.10-plugins-bad[/B] 

[B]gst-ffmpeg

libdvdread4[/B] [B]


Okay, you're not done yet. This next step is essential.[/B]   [B]

Go to Applications / Accessories / Terminal[/B] [B]

Once the Terminal is open type this[/B] [B]

sudo apt-get install libdvdread4[/B] [B]

Once this is done you have another step to do while in Terminal[/B] [B]

[COLOR=Red]sudo /usr/share/doc/libdvdread4/install-css.sh[/COLOR][/B] [B]

Now when this is completed you can close the Terminal.[/B] [B]

Okay, now try to [/B] [B]play the dvd.  If if plays great (mine did not). In that case make sure the Ubuntu  Software mentioned in the first list has been installed. If it has then  repeat the steps for the Terminal. 
You can try it but mine still didn't work. So I shut down, restarted and then it worked. [/B]

And here's a question I have about the advice above: the following is not a command that can be validly issued in a shell (correct?): 

[B]sudo /usr/share/doc/libdvdread4/install-css.sh

[/B]In fact (I think) it's not a command. It starts (sudo) to tell the shell to superuser do something, but then doesn't issue a command, and then finishes with a path and a filename. 

My apologies if I got that wrong. I did try to execute the command, and bash responded with "no such command." Just another note, to those of us who are trying to figure this out: the file **gst-plugins-base **isn't available as an individual download from the Software Center. But I did do a search for it, using "[B]locate gst-plugins-base"

[/B]On my system it's stored here: **/usr/share/locale-langpack/en_GB/LC_MESSAGES/gst-plugins-base-0.10.mo**

So it looks (so far) like I have the required plugins, but I cannot watch Jack Nicolson wonder "What if this is as good as it gets?" 

Help?

---

### Post by Frogs Hair on 2012-04-12
There may be a codec in this repository that might help . [http://www.ubuntuvibes.com/2011/10/medibuntu-repository-now-available-for.html](http://www.ubuntuvibes.com/2011/10/medibuntu-repository-now-available-for.html)

---

### Post by westcoast01 on 2012-04-12
[www.youtube.com/](www.youtube.com/)**watch**?v=dMoYutiUQYU
This helped me. Best of luck.

---

### Post by SeijiSensei on 2012-04-12
> **jps2012 said:**
> sudo /usr/share/doc/libdvdread4/install-css.sh

And here's a question I have about the advice above: the following is not a command that can be validly issued in a shell (correct?):

If you try that you'll see that it works as advertised.

It runs the bash script install-css.sh with administrative ("root") privileges via sudo.  The script downloads the libdvdcss library which handles decrypting commercial DVDs.  It's illegal to distribute this into the US because of the "anti-circumvention" provisions of the Digital Millennium Copyright Act.  So the onus is put on the user to decide whether or not to install the software depending on the state of the law in the user's country and the user's willingness to comply with the law if it is prohibited.  In many parts of the world downloading libdvdcss is perfectly legal, but it's not in the US.  That said, there are thousands if not millions of Americans with libdvdcss on our Linux machines.

---

### Post by SeijiSensei on 2012-04-12
double-post deleted

---

### Post by Frogs Hair on 2012-04-12
I was testing a movie that would not play(Queen of the Dammed)  and I received a message that suggested this package .

```
libdvdcss2
``` This is a medibuntu package. The movie now plays .

---

### Post by uRock on 2012-04-12
Copy and paste the following commands into a terminal to install libdvdcss,

For 32 bit ubuntu, ```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb

sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```
For 64 bit ubuntu,```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb

sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

---

### Post by jps2012 on 2012-04-12
Just wanted to note that I'm not sure WHY the script works, given that I don't SEE a command, but you (SS) taught me a valuable lesson--sometimes commands don't look like commands. Now I have to figure out why that is (so I can execute commands with more confidence).

---


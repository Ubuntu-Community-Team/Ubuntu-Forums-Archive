---
title: "Cannot play a DVD.using VLC media player."
date: 2013-11-14
forum: New to Ubuntu
---

### Post by g.tucker938@btinternet.co on 2013-11-14
I cannot open a specific DVD using VLC media player or Videos, I am running ubuntu 13.10. the video is "Drop Dead Fred" with Rick Mayall, each time I open it, I get a screen full of folders which the computer tells me.
" cannot read media", When I click properties the folders are designated as jpeg, the screen also tells me there are no add  on's  available to play this disc, can anyone help please?

---

### Post by oldos2er on 2013-11-14
Sounds like a problem with the DVD itself, and not your software. Can you verify the DVD works in a different DVD player, or on a different system? Do other DVDs work ok for you?

---

### Post by newb85 on 2013-11-14
Have you already installed libdvdread4 and run the install-css script?

---

### Post by Frogs Hair on 2013-11-14
This package is also helpful . [http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html)

---

### Post by newb85 on 2013-11-14
> **Frogs Hair said:**
> This package is also helpful . [http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html)

Er...yeah, that's what the install-css.sh script installs.  ;)

Edit: to put my initial suggestions in a more helpful format:
```
sudo apt-get update
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by Frogs Hair on 2013-11-14
Thanks, The last time Installed libdvdcss2 was on 13.04 and medibuntu was still up and running. There were no script instructions in post #3 .

---

### Post by g.tucker938@btinternet.co on 2013-11-15
Thank you Ann, The DVD works perfectly on my VCR, but not on the computer.

---

### Post by g.tucker938@btinternet.co on 2013-11-15
Thank you Jane,I have not installed libdvread4, I will try that and see what happens.

---

### Post by g.tucker938@btinternet.co on 2013-11-15
My thanks to all, I have a few things now to try.

---

### Post by newb85 on 2013-11-15
If you don't also install css, proprietary DVDs won't play.

---

### Post by chideock on 2013-11-15
Ensure libdvdread4 is installed
Ensure unbuntu-restricted-extras is installed
Go to videolan.org and click on "libdvdcss" under "for developers"
add the videolan repositories to your "sources.list" (use terminal)
run the wget command (use terminal)
then run "sudo /usr/share/doc/libdvdread4/install-css.sh" (use terminal)

you should be good to go after all that

---

### Post by thesleash on 2013-11-15
personally, i would try using the following command

sudo apt-get update && sudo apt-get install ubuntu-restricted-extras libdvdread4

---

### Post by newb85 on 2013-11-15
The terminal commands I gave in post #5 should be sufficient.   I've done it that way a dozen times. Downloading the css package from the videolan project should be handled by the install-css script. 

Libdvdread4 is part of restricted-extras.

---


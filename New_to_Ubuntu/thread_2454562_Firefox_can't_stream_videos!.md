---
title: "Firefox can't stream videos?!"
date: 2020-12-01
forum: New to Ubuntu
---

### Post by dvill110 on 2020-12-01
My Firefox browser is no longer capable of streaming videos on websites like Netflix, Udemy, or Crunchyroll! 

3 days ago, I wiped my Windows OS from my laptop and switched to Ubuntu for the first time ever. I love it so far and there's no going back! But my understanding of Linux is still very basic, and I don't know how to solve this problem with streaming videos. The ONLY place I can watch videos on the browser is on YouTube for some reason. I googled for solutions, but the only thing I found was to install some codecs (not sure what those are yet) with ```
sudo apt install libavcodec-extra
``` and when I do that, it brings up some Microsoft agreement that I can't move forward with because nothing lets me proceed with the modal! Any advice here??

---

### Post by Dennis N on 2020-12-01
If the videos use DRM content protection, you need to enable **Settings > Preferences > Play DRM Controlled Content**

---

### Post by Impavidus on 2020-12-02
> **dvill110 said:**
> ... it brings up some Microsoft agreement that I can't move forward with because nothing lets me proceed with the modal! Any advice here??
When you encounter some kind of menu in a terminal, try the tab key to select a button and enter to hit it. Other useful keys: arrows, space, escape. The mouse doesn't work in a terminal.

---

### Post by ActionParsnip on 2020-12-02
Does Chrome work OK?

---

### Post by poorguy on 2020-12-02
> **dvill110 said:**
> My Firefox browser is no longer capable of streaming videos on websites like Netflix, Udemy, or Crunchyroll! 

3 days ago, I wiped my Windows OS from my laptop and switched to Ubuntu for the first time ever. I love it so far and there's no going back! But my understanding of Linux is still very basic, and I don't know how to solve this problem with streaming videos. The ONLY place I can watch videos on the browser is on YouTube for some reason. I googled for solutions, but the only thing I found was to install some codecs (not sure what those are yet) with ```
sudo apt install libavcodec-extra
``` and when I do that, it brings up some Microsoft agreement that I can't move forward with because nothing lets me proceed with the modal! Any advice here??

I'm using Ubuntu 20.04.1 and here's all I do to get DVDs to play.

Open the terminal and copy and paste this command then press enter and if needed enter your password.

```


sudo apt install libdvd-pkg

```

When that is finished then copy and paste this command into the terminal and press enter.

```


sudo dpkg-reconfigure libdvd-pkg



```

When finished close everything and restart your computer.

---

### Post by SeijiSensei on 2020-12-02
> **dvill110 said:**
> My Firefox browser is no longer capable of streaming videos on websites like Netflix, Udemy, or Crunchyroll
What version of Ubuntu?

I haven't had a problem playing videos from Netflix or Crunchy for years.

In the Firefox menu, go to Add-ons and make sure the "Widevine" module is set to "Always Activate." Click first on the module, then on the three dots in the upper-right-hand side of the description that appears. Make sure it is set to Always Activate.

You don't need any other software to stream video like libavcodec-extra.

---

### Post by dvill110 on 2020-12-02
Ubuntu 20.04.1 LTS

Chrome actually has no issues. Just checked Widevine and it was already set to Always Activate! No fix.

---

### Post by dvill110 on 2020-12-02
> **Impavidus said:**
> When you encounter some kind of menu in a terminal, try the tab key to select a button and enter to hit it. Other useful keys: arrows, space, escape. The mouse doesn't work in a terminal.

Thanks. I found out that it was an ncurses style menu and the tab thing worked. I accepted the terms and it looks like the issue is solved, I can stream Netflix and Udemy and Crunchyroll. I still don't understand what problem and solution was lol, but it's working now!

---


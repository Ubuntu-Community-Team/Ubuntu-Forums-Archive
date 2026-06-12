---
title: "Firefox 2.0.0.14 in Hardy, why?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by iClouseau88 on 2008-04-24
Hi all,

I have firefox 2 and firefox 3 installed in Ubuntu 8.04.  However, when I either click on firefox 3 or use gksudo firefox &, I only get firefox 2.0.0.14.  Could you show me how to get firefox 3 beta 5?

Thanks in advance.

---

### Post by otrojake on 2008-04-24
Post the output of

```
whereis firefox
```if you please.:)

---

### Post by iClouseau88 on 2008-04-24
> **otrojake said:**
> Post the output of

```
whereis firefox
```if you please.:)

firefox: /usr/bin/firefox /usr/bin/firefox.ubuntu /etc/firefox /usr/lib/firefox /usr/share/firefox

Thanks!

---

### Post by otrojake on 2008-04-24
Could you also do a whereis for firefox-3 and firefox-3.0?  I think that might be the deal.  If you can find where the Firefox 3 execute is, then you should be able to create a launcher for it.  And if that doesn't turn anything up search for firefox in Synaptic to see if Firefox 3 has a different package name than firefox.

---

### Post by glennric on 2008-04-24
It appears that you have made a diversion at some point.  The file /usr/bin/firefox.ubuntu is most likely the one you are wanting.  Try typing
```
sudo dpkg-divert --rename --remove /usr/bin/firefox
```
in a terminal.  Then try to run firefox.

---

### Post by iClouseau88 on 2008-04-24
> **otrojake said:**
> Could you also do a whereis for firefox-3 and firefox-3.0?  I think that might be the deal.  If you can find where the Firefox 3 execute is, then you should be able to create a launcher for it.  And if that doesn't turn anything up search for firefox in Synaptic to see if Firefox 3 has a different package name than firefox.

firefox-3: /usr/bin/firefox-3.0 /etc/firefox-3.0 /usr/lib/firefox-3.0b5

Output for ff 3.0:

firefox: /usr/bin/firefox /usr/bin/firefox.ubuntu /etc/firefox /usr/lib/firefox /usr/share/firefox

Thanks!

---

### Post by otrojake on 2008-04-24
There we go.  If you want to create a launcher in your panel for Firefox 3, just do this.  Right-click on the panel and click Add to Panel and then Custom Application Launcher.  Just type in your information there.  The most important bit is in the command box type:  /usr/bin/firefox-3.0

If Firefox 2 is the default in the menu and you want 3 in your menu, go to System-->Preferences-->Main Menu and click on Internet in the left pane and click New Item.  In that dialog box follow the same steps as above.

That should do it!:)

Also, if you want to run Firefox 3 from the terminal for whatever reason, just type /usr/bin/firefox-3.0

---

### Post by kansasnoob on 2008-04-24
Uh, both are installed by default, which is a good thing I think.

When FF 3 Beta 5 breaks I just let my mouse guide to to >internet & I use Firefox 2.

I'm thinking it will be straightened out very soon.

---

### Post by iClouseau88 on 2008-04-24
> **otrojake said:**
> There we go.  If you want to create a launcher in your panel for Firefox 3, just do this.  Right-click on the panel and click Add to Panel and then Custom Application Launcher.  Just type in your information there.  The most important bit is in the command box type:  /usr/bin/firefox-3.0

If Firefox 2 is the default in the menu and you want 3 in your menu, go to System-->Preferences-->Main Menu and click on Internet in the left pane and click New Item.  In that dialog box follow the same steps as above.

That should do it!:)

Also, if you want to run Firefox 3 from the terminal for whatever reason, just type /usr/bin/firefox-3.0

Hi,
I actually have both icons in the panel: Applications>Internet> FF 2 browser and FF (3) browser.  When I click on either icon, I get the same version 2.0.0.14, not version 3 beta 5.

Also, when I type /user/bin/firefox-3.0 I get version 2.0.0.14.

What should I do next?

---

### Post by otrojake on 2008-04-24
Hmmm...  I think that one's beyond me.  Sorry, but I don't think I can be of much more help with the knowledge I have right now.  Anyone else have any ideas?

---

### Post by iClouseau88 on 2008-04-24
> **glennric said:**
> It appears that you have made a diversion at some point.  The file /usr/bin/firefox.ubuntu is most likely the one you are wanting.  Try typing
```
sudo dpkg-divert --rename --remove /usr/bin/firefox
```
in a terminal.  Then try to run firefox.

Removing `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg-divert: rename involves overwriting `/usr/bin/firefox' with
  different file `/usr/bin/firefox.ubuntu', not allowed

---

### Post by iClouseau88 on 2008-05-01
Hi again,
I figured that firefox in /opt actually refers to FF version 2.0.0.14 so this is what I get when double-clicking FF icon or using the menu. I want beta 5 not 2.0.0.14.  Right now Synaptic Pkg Manager shows firefox and firefox-3.0 are both version 3 beta 5.  I did completely remove firefox-2.0 (i.e. version 2.0.0.14) via Synaptic.  The "firefox" that I just downloaded and installed to my home folder based on the "one-click" tip in Tomsbuntu web page refers to FF 3.0 beta5.  How should I replace firefox in /usr/bin which is linked to /opt/firefox with the one I just downloaded to my home folder?  In other words, how do I replace 2.0.0.14 with 3.0 beta 5?

Thanks a lot for your help.

---

### Post by otrojake on 2008-05-01
First, delete the copies of Firefox in your opt and bin directories.  I'm unsure of the exact code, since I'm not in front of my Ubuntu box right now, but it should be something like this.  Just put in the appropriate paths for where firefox is, but it should be fairly close to this...

```
sudo rm /usr/bin/firefox /opt/firefox
```

Now, since Firefox is now in your home directory create a symbolic link to that copy of firefox for the other two firefox locations.  Again, I'm unsure of the exact locations.  These should be fairly close, but make sure you have the correct directory locations and then run these codes with those locations.
```
sudo ln -s /home/yourname/whereyouputfirefox/firefox /usr/bin/firefox
```
```
sudo ln -s /home/yourname/whereyouputfirefix/firefox/firefox /opt/firefox
```

Hope that helps.

---

### Post by nowshining on 2008-05-01
you can also edit your /etc/bash.bashrc file _ and logout and back-in for it take effect to always launch your desired firefox version, and in the menus, add a new menu entry for firefox 3.x and in the command the location or command to launch it.

for aliases

alias top='htop'

add that and change top to the program firefox and htop to rhe desired item you'd like to launch, just add the alias line anywhwere you want. To add a comment add a # in front of the description.

Ex:

#launch in terminal firefox3 and not firefox2
alias firefox='firefox3'

---


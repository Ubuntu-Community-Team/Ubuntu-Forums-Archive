---
title: "How to switch from Unity shell to Gnome shell, in Ubuntu"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by Janas on 2012-02-26
Hi guys,

I am new to the forums, and I thought I would post this up first, since I had problems and this helped me.

Want to switch between Unity and Gnome shells in Ubuntu? Here's how:

Open the Ubuntu Software Center by pressing meta + 6. Search for "Gnome shell." Click on the Gnome shell and download it. 

After Gnome shell has finished downloading, you must install it. Double click on the Gnome shell item under the Progress tab. Click on the "Install" button. The USC will do the rest of the work for you.

Now Gnome shell is installed, but it doesn't switch over automatically. What you must do is log out of your session, then log back in. After you log out, and before you enter your password, you will see a clockwork/gear icon in the upper right of the log-in window. Click on this, then select "Gnome." When you log back in, your shell will be switched over to the Gnome shell!

Note: If you have the "Auto Login" option enabled in User Accts, you must disable this, or it will automatically switch you back to Unity. This was the hiccup I ran into. So disable Auto Login to enable the Gnome shell.

That's it! Hope it helps!

EDITED:

Hey guys, it looks like I ran into yet another glitch using this method (sigh facepalm). Still not totally bug-free, but not a dealbreaker. If you cannot shut down the PC after making the change and Ubuntu only logs out, this fixes it (sorry for my bad instructions):

I found a possible solution to this bug. It has something to do with  the auto login >function in the user management from Unity. When  activated it cannot shutdown anymore. >Also disable the auto login is  not possible anymore.
      What I did:   gksudo gedit /etc/lightdm/lightdm.conf
      remove the line:   autologin-user= YOUR USERNAME
      Restart your computer with:   sudo shutdown -h now
      
After that I had a system that worked normally again.

---

### Post by PaulW2U on 2012-02-26
And don't forget to go to [http://extensions.gnome.org/]("http://extensions.gnome.org/") while using Firefox for some very useful Gnome Shell extensions such as drop-down menus, a task-bar and workspace indicators. ;)

*Edit: This will not work with early versions of Gnome Shell.*

---

### Post by matbluvenger on 2012-02-26
Just tried this for the first time. So far I really enjoy it. Now I'm going to have to read up on it now... yay more reading! :D

---

### Post by matbluvenger on 2012-02-26
Oops, for some reason I can't install the extensions you posted, Paul. And if I go to "System Info" it doesn't tell me what version of GNOME I'm using. In the Log-In lost I opted for "GNOME" instead of "GNOME Classic." Should there have been a "GNOME3" option if all went as planned?

---

### Post by PaulW2U on 2012-02-26
> **matbluvenger said:**
> Oops, for some reason I can't install the extensions you posted, Paul. And if I go to "System Info" it doesn't tell me what version of GNOME I'm using. In the Log-In lost I opted for "GNOME" instead of "GNOME Classic." Should there have been a "GNOME3" option if all went as planned?

What version of Ubuntu are you using?

---

### Post by matbluvenger on 2012-02-26
> **PaulW2U said:**
> What version of Ubuntu are you using?

Oh, sorry. 11.10

---

### Post by PaulW2U on 2012-02-26
> **matbluvenger said:**
> Oh, sorry. 11.10

Then as far as I can remember, I don't have that version installed at the moment, you select Gnome when you log-in and when on the site if there are any extensions that are incompatible you will get an indication that says so. You must use Firefox and have the appropriate extension installed. Did you get a prompt to install it?

---

### Post by matbluvenger on 2012-02-26
I haven't even tried installing the extensions because on every page I go to on the extensions website (even the homepage) I get a big red bar on the top that says "You do not appear to have an up to date version of GNOME3. You won't be able to install extensions from here. See the about page for more information"

and on the about page it says this:
> Support for installing extensions from this website was first added in GNOME 3.2, so if you are using GNOME 3.0, you'll need to upgrade to a newer Linux distribution. You can check what version of GNOME is installed on your system using the "System Information" panel of "System Settings". If you are using GNOME 3.2 or newer and installation still doesn't work, check to make sure that the "GNOME Shell Integration" plugin is installed and enabled in your browser preferences.

If you are behind a proxy, make sure you have configured your proxy in both your browser's configuration dialog as well as GNOME's Network panel under System Settings. GNOME Shell Extensions needs both settings panels configured for the one-click installation to work.

Note: there were some bugs in the browser plugin shipped in some versions of GNOME 3.2 that prevent it from working properly under WebKit-based browsers like Epiphany and Chromium. GNOME Shell 3.2.2.1 has fixed these problems, so make sure you are using it.

---

### Post by PaulW2U on 2012-02-26
Oops, It looks like you'll have to wait for Ubuntu 12.04.

Sorry for wasting your time. :oops:

---

### Post by matbluvenger on 2012-02-26
Oh, no sweat. I was just curious ^_^  I'm more than happy to wait for 12.04!

---


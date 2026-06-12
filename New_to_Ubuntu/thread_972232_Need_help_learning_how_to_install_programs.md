---
title: "Need help learning how to install program/s"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by faron45 on 2008-11-05
Can someone please explain to me how to install the firefox pkg. that I downloaded from the internet onto my desktop ? I thought I had the latest version but every time I tried to go to my hotmail acct. it was continually asking me to upgrade my browser so that all functions of hotmail would work.And,now, hotmail has "upgraded" itself again & I cannot seem to reply to or even write emails.I get no cursor in the compose field.

[All this was due to my trying to use an even older version of firefox so that I could use another program that I downloaded as this program would not work with the latest version of firefox.I've recently completely deleted the older version of firefox].

 So,I've finally downloaded the latest version of firefox to my desktop.....Now,I'm just not sure how to go about correctly installing it.I've been using pc's for a little while but,I'm fairly inexperienced with the download/install aspect of it still.

When I right click on the icon on the desktop to prepare to install,the pc gives me the options to...open with archive mgr...open with other app..........extract here.........extract to..........copy.....cut.......delete,etc ! Hellllllllpppppppppp !!

Also,I would have thought that I should have been up to date anyway seeing as my update mgr. seems to be operating properly & I always do the updates when I see that they are available.So,what gives ?? Arrrrgghhhh !

        Help please !!
                Tank-u !!!

---

### Post by Zalbor on 2008-11-05
Hotmail asking you to upgrade your browser just means microsoft won't admit they specifically made hotmail to only work 100% with internet explorer. In short: Nothing wrong with your firefox.

You usually install programs using one called "Synaptic package manager", which should be somewhere in your menus. Keep that in mind for the future.

---

### Post by wardrich on 2008-11-05
open your terminal and type:

sudo apt-get install firefox

As for other programs:

sudo synaptic.

Synaptic will give you a list of all sorts of programs you can easily install and uninstall.

---

### Post by mrtomservo on 2008-11-05
You can try getting an add-on that tricks web pages into thinking you're running another OS/browser combo.  In Firefox, try going to Tools, Add-ons, and search for 'user agent'.  You should see User Agent Switcher, install it and you may have to restart Firefox.  Then under Tools, go to User Agent Switcher and select the variety you'd like.

---

### Post by faron45 on 2008-11-05
Zalbor-Yes,I realize ms is bs [ha ha] & generally I do use Synaptic.Thank you though.
wardrich-If I do this your way will it install the latest version [from my desktop] as I'm afraid the version in synaptic may not be up to date ?.....Thank you.

---

### Post by mrtomservo on 2008-11-05
Open up the tar.gz file for Firefox you've downloaded and uncompress it to where you like.

Open up a terminal and type:

```
sudo apt-get install build-essential
```

Then:

```
apt-get build-dep firefox
```

Continuing in the terminal, change to the directory where you put your Firefox source, and type:

```
./make
```

You may or may not have to type:

```
./make install
```

Hope that helps a bit.

---

### Post by faron45 on 2008-11-05
mrtomservo-I've right clicked on the file on the desktop & it says it's a tar.bz file....And,as I have noted already...when I right click it gives me the options to ...open with archive mgr...open with other app..........extract here.........extract to.........I am confused about how to go about this.

---

### Post by mrtomservo on 2008-11-05
Ok, so right click on the archive, and select extract here.  It should create a folder named firefox or something of the like in the directory where the archive is located.

---

### Post by Paqman on 2008-11-05
I'd recommend *strongly against* installing your browser from outside the repos.

If you do, you won't get any security updates, which are very important for a browser. Seriously, stick to the properly packaged Firefox available through Synaptic or Add/Remove.

The annoying message from Microsoft about upgrading your browser is not a sign that anything is wrong. It's just Microsoft trying to make life difficult for people who aren't using their products.

---

### Post by cardinals_fan on 2008-11-06
The short version: Hotmail is lying.

The long version: Hotmail will never be happy with your browser until you use Internet Explorer.  The [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59") might help trick Hotmail into thinking that you use IE.

---


---
title: "HOWTO: Fix Firefox Controls under Gutsy"
date: 2007-10-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Dudley Innocent on 2007-10-24
I'd like to first pay respect to the original tutorial which can be found [here]("http://osnovice.blogspot.com/2007/05/firefox-controls-are-ugly.html").

**If you are using Ubuntu 7.04 I suggest you visit the [original tutorial]("http://osnovice.blogspot.com/2007/05/firefox-controls-are-ugly.html").**

**So, now if you're using Ubuntu 7.10 Gutsy Gibbons then proceed:**

**Here's the before:**
[CENTER][IMG]http://bp2.blogger.com/_QAACnRmWj_A/RlW_LkOBoHI/AAAAAAAAAGc/Ekeo6Ju8QGY/s400/ugly+radio+buttons+if+firefox.png[/IMG][/CENTER]

**and the after:**
[CENTER][IMG]http://bp2.blogger.com/_QAACnRmWj_A/RlXA-kOBoKI/AAAAAAAAAG0/KmVxN2YV0fU/s400/screenshot3.png[/IMG][/CENTER]

I've found that if you know what the commands are doing, you'll remember them easily. So, here's a run down of what the commands will do.

**WGET** will download the archive to our current directory (*if you had just opened terminal, it will download to your home directory*)

**TAR** will unpack the files from within the package.

**SUDO + command** will prompt you for the *root password* because the **command** most likely deals with files and folders that only *root* may edit.

**CP** simply copies the file from the *left* of the middle space to create the file on the *right* of the space.

**CAT | TEE --APPEND** opens the file on the left of the | and TEE takes that opened file and appends to the next file.

**RM -rf** simply removes an entire directory that you request.
[I]
So without any further wait, copy and paste this in it's entirety into your terminal and enter your root password when it prompts.[/I]

```
wget http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz

tar -xvzf firefox-form-widgets.tar.gz

sudo cp /usr/share/firefox/res/forms.css /usr/share/firefox/res/forms.css.bak

cat firefox-form-widgets/res/forms-extra.css | sudo tee --append /usr/share/firefox/res/forms.css > /dev/null

sudo cp -r firefox-form-widgets/res/form-widgets /usr/share/firefox/res

rm -rf firefox-form-widgets
```

**You may substitute the entire wget command for downloading the attached archive into your home folder**(*/home/username*).

Feel free to reply with any fixes to any mistakes I've made. Thanks!

---

### Post by kaiwan on 2007-12-14
nothing happens when following your instruction ....

---

### Post by Bandicoot on 2007-12-14
Is this different from what is done here: [http://ubuntuforums.org/showthread.php?t=369596&highlight=widgets](http://ubuntuforums.org/showthread.php?t=369596&highlight=widgets)  ??

---

### Post by gammyhand on 2007-12-15
Worked great for me. You need to restart firefox to see the changes by the way.

---

### Post by steveneddy on 2007-12-17
Perfect, thank you.

:popcorn:

---

### Post by smithberry on 2007-12-17
> SUDO + command will prompt you for the root password because t

Just nit picking but sudo asks for your **own** password (and as long as your  user is on the sudo list of folk) will then run the command with root privileges,

Other than that great post, and worked for me.

---


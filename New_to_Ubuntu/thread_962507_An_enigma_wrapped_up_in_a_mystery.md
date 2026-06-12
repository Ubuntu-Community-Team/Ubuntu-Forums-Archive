---
title: "An enigma wrapped up in a mystery"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Langstracht on 2008-10-29
I understood that, in Ubuntu, the command:

   apt-get install gimp

would snag me the latest stable version of Gimp.

Which I understand to be 2.6 - I am running 2.2.

However when executing the command I get

      "Reading package lists... Done
       Building dependency tree... Done
       gimp is already the newest version.
       0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

Anyone know what's going on and how I might/could fix it?

---

### Post by halitech on 2008-10-29
depending on what version you are running, 2.2 might be the latest stable release in the repo for your version. If this is the case, running sudo apt-get install gimp will just confirm you have the latest version. If you want/need a version newer then in the repos, you will need to manually download it and install and update it yourself.

---

### Post by The Cog on 2008-10-29
What version of Ubuntu are you on? Hardy uses gimp 2.4.something.

Once a version of Ubuntu is released, there are no more feature updates to that version, only security updates. This is to avoid breaking things.

You may find a later version of gimp if you enable the backports repositories, which are where later versions of apps get ported backwards to older versions of Ubuntu (sometimes).

---

### Post by Langstracht on 2008-10-29
Thanks for your immediate responses.

I'm a bit embarrassed to admit that I am still with Dapper.  Why you may well ask.  Well, it runs just fine, and I am, probably needlessly, concerned about losing data if I do the 8.04 update and, depending on how charitable you are, either too busy or too lazy to document all the detritus of passwords, accounts and so on AND back up everything (the important stuff is, the less so not).

So it would appear that until I motivate myself to do so, I am stuck with 2.2.  Yes?

Pity.

But thanks for your much appreciated input.

---

### Post by Sarmacid on 2008-10-29
You don't have to stay with version 2.2 just because that's the one in the repositories. As halitech stated, you can get newer versions, but you'll have to manually install and update them.

---

### Post by halitech on 2008-10-29
if for the most part, dapper is doing what you need, no need to upgrade.... yet. Desktop support for 6.06 will expire in June 09 so you will need to upgrade before then. If you want to upgrade Gimp, you can do so manually by downloading the install file from gimps website.

---

### Post by timcredible on 2008-10-29
fwiw, the next time you install ubuntu, create a separate partition for /home (which is where your accounts, data, passwords, etc. reside).  from then on, when you install a newer version, you can leave /home alone and keep all your data, passwords, etc. as-is.  it makes installing new versions much easier.

---

### Post by Langstracht on 2008-10-29
Sorry, yes I did read about that I had the "manual install" option.  

However, in general, this is not something I've had good success with (put it down to aging, dyslexia, inability to follow instructions, stupidity, ...) whereas, as one would expect, I have never had a problem with, if you will, automatic installs.

Guess I have eight months or so before I HAVE to belly up to the bar, so to speak.

Thanks again.

---


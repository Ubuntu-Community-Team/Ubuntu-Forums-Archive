---
title: "Thunderbird crashes on boot"
date: 2011-08-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rv65 on 2011-08-25
Whenever I go into thunderbird, it just simply crashes. I can't even read my email. I do use my ISP's webmail, but this is getting ridiculous. Any help would be great.

---

### Post by rv65 on 2011-08-25
I use the Gnome Classic UI as well aka gnome-panel. Maybe that is the culprit, as there is something in thunderbird that is causing it not to work with gnome classic.

---

### Post by pressureman on 2011-08-25
I didn't have any problems with TBird 7 crashing per se (on gnome shell), but since it's not compatible with Lightning calendar plugin at the moment, I reverted to TBird 6.

I know that oneiric is a beta release, but IMHO, using alpha versions of TBird is a bit too risky.

---

### Post by chrisccoulson on 2011-08-25
> **pressureman said:**
> I didn't have any problems with TBird 7 crashing per se (on gnome shell), but since it's not compatible with Lightning calendar plugin at the moment, I reverted to TBird 6.

I know that oneiric is a beta release, but IMHO, using alpha versions of TBird is a bit too risky.

It's not an alpha version of Thunderbird, so I've no idea where you got that idea from

---

### Post by pressureman on 2011-08-25
> **chrisccoulson said:**
> It's not an alpha version of Thunderbird, so I've no idea where you got that idea from

Is TBird 7.0b1 released yet?

---

### Post by chrisccoulson on 2011-08-25
> **pressureman said:**
> Is TBird 7.0b1 released yet?

No, not officially. I've uploaded the b1 candidate slightly earlier to meet our beta freeze. But this is the b1 release unless there are any show-stopper bugs which would require a respin (unlikely).

---

### Post by pressureman on 2011-08-25
> **chrisccoulson said:**
> No, not officially. I've uploaded the b1 candidate slightly earlier to meet our beta freeze. But this is the b1 release unless there are any show-stopper bugs which would require a respin (unlikely).

Call me pedantic, and however unlikely a respin is, but until it's tagged as beta1, it is still, IMHO, alpha code.

---

### Post by Harry33 on 2011-08-25
> **pressureman said:**
> I didn't have any problems with TBird 7 crashing per se (on gnome shell), but since it's not compatible with Lightning calendar plugin at the moment, I reverted to TBird 6.

I know that oneiric is a beta release, but IMHO, using alpha versions of TBird is a bit too risky.

Thunderbird is beta now,
however, Oneirc is still alfa3.

---

### Post by chrisccoulson on 2011-08-25
> **pressureman said:**
> Call me pedantic, and however unlikely a respin is, but until it's tagged as beta1, it is still, IMHO, alpha code.

Sorry, this is complete rubbish. Can you please stop spreading false information around.

---

### Post by pressureman on 2011-08-25
> **chrisccoulson said:**
> Sorry, this is complete rubbish. Can you please stop spreading false information around.

How am I spreading false information? I'm not the one calling a build-candidate a beta. Sorry if this hurts your feelings, but I believe in being straight up with people.

---

### Post by pressureman on 2011-08-25
> **Harry33 said:**
> Thunderbird is beta now,
however, Oneirc is still alfa3.

Fair point, Oneiric is technically still alpha phase, not beta as I previously said. I had no problems at all with TBird 6, and have previously run TBird betas for reasonable lengths of time.

There's a good reason why they call their alphas "shredder" though, as I've had on a couple of occasions my mailbox trashed by an alpha release of TBird.

---

### Post by SeijiSensei on 2011-08-25
Returning to the OP's original question, you might try forcing a rebuild of your configuration.  Shut down all instances of Thunderbird, then open a terminal and enter this at the "$" prompt (without the "$" of course):

```

$ cd
$ mv .thunderbird .thunderbird.old
$ thunderbird &

```

The first of these moves to the top of your home directory.  The next command moves your current TBird configuration and folders into a safe place.  The last command runs the current version of Thunderbird as a separate process (the "&" operator).

TBird should ask you again for your email configuration.  After you enter your account information, does it work?

[rant]
Firefox and Thunderbird provide essentially no debugging information when run from the command prompt.  I've been left scratching my head on a number of occasions wondering why one or the other doesn't start.  I know to remove the "lock" and ".parentlock" files from my configuration folders, but when that doesn't fix the problem, I'd love to see some more debugging information.  It's as though the Mozilla Foundation decided to ignore its *nix roots and treat programs the way Windows does, hiding useful information from the person running the program.[/rant]

---


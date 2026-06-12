---
title: "Update problem"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by sarum on 2013-02-01
Hi,  I'm an elderly newby on the latest LTS. I like to keep it all up to date.
I've about 50 updates pending, and for the first time I'm confronted with a message saying that there are some updates NOT SOMETHING or other.
I click on OK but I get the same message again.
So; if the updates are there for the taking, right or wrong. There's no choice.
Help please Sarum

---

### Post by ibjsb4 on 2013-02-01
In terminal

```
sudo apt-get update
```

And please post the something or other  :)

---

### Post by Bucky Ball on 2013-02-01
> **ibjsb4 said:**
> In terminal

```
sudo apt-get update
```

And please post the something or other  :)

+1.

After the above command immediately run:

```
sudo apt-get upgrade
```

... and report that something too. This will not update the release, just everything installed in it if it needs it. Sounds like something is being held back and this will probably fix it.

After the upgrade command you may need to run the update one again (you will be informed of new updates because after the upgrade they will be able to be installed).

---

### Post by NikTh on 2013-02-01
Additionally  to the above messages.. 

_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by grahammechanical on 2013-02-01
Is the message "some updates are held back?" I think that I got that yesterday on 12.04. I cannot be sure as I do not use my 12.04 install every day. I am normally using a development version.

You should be able to press continue and update whatever is available. Or wait another day and then see what Update Manager wants to do.

Sometimes packages (libraries) have to be updated together to install correctly. Sometimes some of these packages are not ready to be put into the repositories. So, they are marked as 'held back.' I may be wrong but this is how I understand this situation.

Regards.

---

### Post by sarum on 2013-02-01
Thanks for your help, and apologies for the 'something or other' = 
"requires installation of untrusted pacages"
I've always thought that if it came from Ubuntu it'd be OK and I'm willing to take the risk. But it's impossible to tell the computer 'yes go ahead'
Anyway I've not yet done the CLI you suggested. I'll do it this evening and hope to post a 'solved' together with my thanks.............sarum

---

### Post by NoBugs! on 2013-02-01
That error usually means you have checked an update from a PPA update channel that doesn't support encryption. So you wouldn't know if it was a good package or man-in-the-middle attach.

---

### Post by sarum on 2013-02-02
Hi again,so I did the CLI;.......Update first and got 6 pages of mainly paragraphs starting either 'err' or 'failed'
Then I did the CL '.....upgrade' and got 7 pages of some very positive stuff resulting in my computer being updated.
Back to the update manager and there were 5 new updates which have now been loaded and my computer is now up to date.
I'll not mark this 'solved' in case any of you want to see 13 pages of Terminal. Not too sure how to post so much, but I'll have a go if you want.
Once again I'm left wondering, Ubuntu is OK but it's this forum that makes it good for me.
Thankyou all.............sarum

---

### Post by srekcahrai on 2013-02-02
```

sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

```

---


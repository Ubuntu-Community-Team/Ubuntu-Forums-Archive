---
title: "can anyone help with this system pop up?"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by ringo00 on 2012-09-08
hi all 
does anyone know what the heck ( :P ) is the  pop up sigh i get from my system?  (attached pic)
i'm running ubuntu 12.04 
not sure if its an os pop up or something that my laptop pops up.

---

### Post by pqwoerituytrueiwoq on 2012-09-08
i am guessing the correct icon is missing in your icon theme

---

### Post by ringo00 on 2012-09-08
hello there,
this is the pop up i get. this "forbidden" sign the circle with the line across it. 
any idea what this is?

---

### Post by jerrrys on 2012-09-08
> **ringo00 said:**
> hello there,
this is the pop up i get. this "forbidden" sign the circle with the line across it. 
any idea what this is?

Has this install worked at all?  What kind of laptop?  If it has worked, have you changed anything?

---

### Post by ringo00 on 2012-09-08
the installation worked properly. i started  getting this pop up a couple days ago and i cant figure what is triggering it. i have notice tho that for the time this pop up is on (it is appearing from 1 sec to 4-5 secs tops then it disappears) i cant use the keyboard. (i havent figure any other miss-functions so far while this pop up appears)
the laptop is an acer aspire 6530
the installation is about 10 days old.
i'm guessing that it must be a compatibility issue between my laptop and the os. not sure tho because it didnt appear from the day 1 of the installation.

btw thank you for your quick replies.

---

### Post by jerrrys on 2012-09-08
Open a terminal and enter:

sudo apt-get update

Get any errors?  If not, enter:

sudo apt-get upgrade

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by ringo00 on 2012-09-08
run them both without errors,
now i'm trying to use everything i use in my daily routine to see if it pops up again.
i will let you know.
thank you so much.

---

### Post by ringo00 on 2012-09-09
hi all again,
after doing the 
sudo apt-get update and 
sudo apt-get upgrade the problem seems to be gone but today i opened my laptop and before i manage to do anything it kept appearing the same pop up 
i'm attaching a new photo in case it helps. 
thank you in advance.

---

### Post by Raphicerus on 2012-09-09
I can repeatably get it to appear for ~ 5 seconds by hitting the go/pause key on the top of my keyboard - the key that looks like this: 

    |> / ||

My laptop is a Sony VAIO and the keyboard a Microsoft Wireless one, if it matters.

---

### Post by coldcritter64 on 2012-09-09
OP, I can bring that symbol up here if I press the multimedia keys "Previous", "Next" or "Pause/Play" when no media player is operating. If a player supporting those functions is running through a playlist the keys work fine. Seems like a notification to inform you that a key press can't be processed at the time. I'm on a desktop install by the way.

See the screenshot below.

---

### Post by ringo00 on 2012-09-09
so true. i manage to bring that symbol up on demand by pressing the multimedia buttons "next" and "previous" with no media player operating. its seems like a notification to inform you that a key press cant be processed at the time in deed. but the weird thing is that this symbol appears without  me pressing any keys of the  keyboard at all.
anyways thank you so much for the help at least i have a clue of whats going on

---

### Post by newb85 on 2012-09-09
Those media keys can interface with several media programs.  If none of those programs are running, the system doesn't know which one to pass the command to, so it shows you that notification to let you know that command is unavailable.

Open something like Banshee, Rhythmbox, or Pithos, and you will find the media buttons no longer throw up that notification, because they actually do something.

---

### Post by ringo00 on 2012-09-09
OK PROBLEM SOLVED.
it was a miss functional key on my laptop (it has touch multimedia buttons and one of them it was broken so it pressed itself at random times) thats why i didnt know what it was triggering it. i disabled ( the hard way :P ) the button and everything is ok.
Thank you so much everyone who dig into it for your time.

---

### Post by newb85 on 2012-09-09
Please mark this thread as solved.

---


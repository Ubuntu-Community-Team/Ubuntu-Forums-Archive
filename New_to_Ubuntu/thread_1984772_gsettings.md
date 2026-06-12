---
title: "gsettings"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-05-22
I was reading this article from PC magazine that says
"Our only gripe is with the fiddly pop-up scroll bars, but you can get rid of these with the gsettings shell command."

Now I want to use gsettings but don't know how, it is installed but when I type gsettings in the terminal I see no option about scroll bars.Here is a link to the article, thanks

[http://www.pcpro.co.uk/reviews/software/374647/ubuntu-12-04-lts]("http://www.pcpro.co.uk/reviews/software/374647/ubuntu-12-04-lts")

---

### Post by wojox on 2012-05-22
It should be dconf-editor. 
```
sudo apt-get update; sudo apt-get install dconf-tools
```
Alt+F2
```
dconf-editor
```
Then go to org > gnome > desktop > interface > ubuntu-overlay-scrollbars > false

---

### Post by cmcanulty on 2012-05-22
thanks I had dconf installed but couldn't find the scrollbar setting. However mine gives a choice of checking or unchecking not true or false. Which option turns them off?

---

### Post by wojox on 2012-05-23
> **cmcanulty said:**
> thanks I had dconf installed but couldn't find the scrollbar setting. However mine gives a choice of checking or unchecking not true or false. Which option turns them off?

Checked is on (true),
Unckecked is off (false).:p

---

### Post by cmcanulty on 2012-05-23
thanks solved

---

### Post by CraigThomas on 2012-06-25
I haven't tried it yet, but this link may be useful to anyone else stumbling across this thread:

[http://www.liberiangeek.net/2012/03/disable-ubuntu-overlay-scrollbars-in-ubuntu-12-04-precise-pangolin/]("http://www.liberiangeek.net/2012/03/disable-ubuntu-overlay-scrollbars-in-ubuntu-12-04-precise-pangolin/")

It suggests typing:

```
gsettings set org.gnome.desktop.interface ubuntu-overlay-scrollbars false
```

Hope this helps.

---

### Post by CraigThomas on 2012-06-26
Confirmed.  The gsetting command in the last post worked for me (once I restarted any already open windows, including my terminal one)

---

### Post by MG&amp;TL on 2012-06-26
My understanding is that dconf editor can access Gsettings keys...so is it not just the same thing in CLI format?

---

### Post by cmcanulty on 2012-06-26
It would be great if someone could post a gsettings guide. It is very hard to find where things are hidden now.

---

### Post by MG&amp;TL on 2012-06-26
> **cmcanulty said:**
> It would be great if someone could post a gsettings guide. It is very hard to find where things are hidden now.

Guess it's just a matter of experimenting. Dconf-editor is good, but it would be great if it had a search function.

---

### Post by cmcanulty on 2012-06-26
yes there isn't even a help tab and stuff seems to be in unintuitive locations

---


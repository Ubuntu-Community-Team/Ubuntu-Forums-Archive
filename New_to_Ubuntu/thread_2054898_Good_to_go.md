---
title: "Good to go ?"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by jdw77 on 2012-09-08
Having my bank account hacked was the final straw for me to make the switch to Ubuntu and after wrestling with with wifi drivers for a few days I'm now running vanilla 12.04 on my ancient laptop.
Am I now safe to start doing on-line banking without hunting down and installing extra security / firewall / anti-malware software  etc ?

---

### Post by vasa1 on 2012-09-08
Ask the mods to move your question to the "security" section. There'll be quite a few responses letting you know exactly how "good to go" you are.

---

### Post by Bachstelze on 2012-09-08
It depends on how exactly your account was "hacked"... You can surf without worrying about malware, but no OS can save you from yourself.

---

### Post by hakermania on 2012-09-08
> **Bachstelze said:**
> It depends on how exactly your account was "hacked"... You can surf without worrying about malware, but no OS can save you from yourself.

Wow! Nicely said!

What Bachstelze means is do not expect an OS to prevent you for example to send an email with all your personal sensitive information to the whole web. Generally: Do not make *silly* actions.

Do not blindly run commands, be careful of phishing pages (**always** look the url for validity before logging into a website), do not give out sensitive information like your IP, do not click on random banners, do not  visit "weird" sites that  may harm your computer etc.

Ubuntu will protect you very well from others, but this does not mean that it will not let you to do anything you want.

---

### Post by jdw77 on 2012-09-08
#3 & #4 Hmm...
thanks for your sage advice o great ones ):P

---

### Post by Epodx64 on 2012-09-08
Linux is inherently more secure then Windows however no O.S. is full-proof. When your account got hacked was it because you where using a weak password? I suggest going over your passwords and tightening them up don't use the same one for anything and a good way to start making strong passwords is take two random license plate numbers and put them together something like this rXD#%3o2k something like that never use a word in any language especially never use names birth dates pets names etc... after you've strengthen your passwords make sure ufw is enabled just boot up a terminal and type 
sudo ufw-enable 
It's a basic firewall but gets the job done for the most part you can also install Firestarter if you'd feel more comfortable with a GUI always present
sudo apt-get install firestarter
Another big thing is pay attention to where you're keeping sensitive files on programs like Limewire the most searched for items are things like "wells fargo" "chase" "taxes" people tend to just save everything to one place and if that one place is being shared through P2P software well you get my point. Really good security just comes down to common sense and being aware if a website wants your social or CC# to register you for something really think twice about it. One final bit of advise if your using Firefox or Chrome install Flashblock and AdBlock.

That's about it in a nutshell. Hope some of my advice helps.

oh yeah, and if someone gives you a strange command to run in a terminal be careful because all it takes is one sudo rm command and your filesystem is gone.

---

### Post by hakermania on 2012-09-08
> **Epodx64 said:**
> a good way to start making strong passwords is take two random license plate numbers and put them together something like this rXD#%3o2k something like that never use a word in any language especially never use names birth dates pets names etc...
[http://xkcd.com/936/](http://xkcd.com/936/)

---

### Post by Epodx64 on 2012-09-08
License plates are good way to remember your password but hard for a computer to guess since there isn't any type of word associated with them and there basically 12 Random digits start off with something like &-Ro0zMM^uI0z+- I don't think brute force is going to get that one and I said using any word from any language is generally a bad idea. I've noticed people are pretty lax with passwords in general though if they have a dog named maggie and there birthday is 10/30/80 theres a pretty good chance that there email,health records,bank account,etc... can all be accessed with some combination of Maggie103080 or Maggie1980 etc... pretty reckless to entrust you're bank account to something as simple as Maggie1980

---


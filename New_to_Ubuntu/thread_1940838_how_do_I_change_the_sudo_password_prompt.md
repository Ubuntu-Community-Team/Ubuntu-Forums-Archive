---
title: "how do I change the sudo password prompt?"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by AnojiRox on 2012-03-14
hi,

I like to change EVERYTHING:p and I was wondering if there was a way to change the bash sudo password prompt. for the moment it's this
```
[sudo] password for anojirox:
```and I want it to be this
```
what's your password? please enter it here:
```thx in advance!;)

---

### Post by tbhatia4 on 2012-03-14
> **AnojiRox said:**
> hi,

I like to change EVERYTHING:p and I was wondering if there was a way to change the bash sudo password prompt. for the moment it's this
```
[sudo] password for anojirox:
```and I want it to be this
```
what's your password? please enter it here:
```thx in advance!;)

Lol @ your Request 
btw i don't think you can do that

---

### Post by AnojiRox on 2012-03-14
I've found a way:)
I put this into my .bashrc file:
function dosu () {
sudo -p "What's your password? please enter it here: " $1 $2 $3 $4 $5 $6 $7 $8 $9
}

---

### Post by tbhatia4 on 2012-03-14
> **AnojiRox said:**
> I've found a way:)
I put this into my .bashrc file:
function dosu () {
sudo -p "What's your password? please enter it here: " $1 $2 $3 $4 $5 $6 $7 $8 $9
}

Great :popcorn:

---

### Post by sudodus on 2012-03-14
Maybe you can also learn making an ***alias***. There are already some simple aliases in .bashrc.

```
alias sudden='sudo -p "What'\''s your password? please enter it here: " '
```

And now, please mark this thread as SOLVED (click **[COLOR="Red"]Thread Tools[/COLOR]** at the top of this page)

---

### Post by jag3dagster on 2012-07-10
This post is fantastic!

It makes me so happy to know that there are customizers out there that have the same customization wants and needs that I do.

Many thanks :KS

---


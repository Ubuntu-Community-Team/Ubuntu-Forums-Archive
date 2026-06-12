---
title: "Some scripting Problems"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by thedawg on 2013-02-27
Hi there, so I have an almost perfect running script, but at one point there is an If statement, in which I'm declaring a variable 
[
                   if  [ "$(lspci | grep -i vga | grep -i -o nvidia)" != "" ]
                   then
(line 16)              $pkg = nvidia
]

Now I get always the error :" line 16: =: command not found "
tried using the == or putting nvidia in "" 

hope someone has an Idea how to maybe fix it

greetz 
thedawg

---

### Post by Drenriza on 2013-02-27
> **thedawg said:**
> Hi there, so I have an almost perfect running script, but at one point there is an If statement, in which I'm declaring a variable 
[
                   if  [ "$(lspci | grep -i vga | grep -i -o nvidia)" != "" ]
                   then
(line 16)              $pkg = nvidia
]

Now I get always the error :" line 16: =: command not found "
tried using the == or putting nvidia in "" 

hope someone has an Idea how to maybe fix it

greetz 
thedawg

Wouldn't a better way be.

```

if [ ! -z "$(lspci | grep -io -e "vga" -e "nvidia" )" ]
then
#Something
fi

```-z means. String is null
[http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html)

Not a scripting expert so if anyone has input to my suggestion. Please don't hold back :)

---

### Post by thedawg on 2013-02-27
Sorry my fault, of course I've closed it in the end ;) 
didn't think the rest would be needed.
Here's the whole if statement where the failure appears

if  [ "$(lspci | grep -i vga | grep -i -o nvidia)" != "" ]
then
        $pkg = nvidia
        apt-get install  nvidia-current nvidia-current-updates
else if
    [ "$(lspci | grep -i vga | grep -i -o intel)" != "" ]
then
        $pkg = intel
else
        $pkg = ati

fi
fi

---

### Post by fdrake on 2013-02-27
try this, and please use code tags:

change "(line 16) $pkg = nvidia" to "pkg = nvidia";

you are assigning a variable not calling it, therefore you do not need the "$" in fron of it

---

### Post by thedawg on 2013-02-27
Did not work :( 

still getting 

" line 16: pkg = nvidia: command not found "

---

### Post by fdrake on 2013-02-27
> **thedawg said:**
> Did not work :( 

still getting 

" line 16: pkg = nvidia: command not found "
```
if [ "$(lspci | grep -i vga | grep -i -o nvidia)" != "" ]
then
pkg="nvidia"
apt-get install nvidia-current nvidia-current-updates
else if
[ "$(lspci | grep -i vga | grep -i -o intel)" != "" ]
then
pkg="intel"
else
pkg="ati"

fi
fi


```

bash complains about the empty spaces arount "="

---

### Post by thedawg on 2013-02-27
That's it,
thanks fdrake

---


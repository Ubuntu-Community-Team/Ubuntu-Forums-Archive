---
title: "Shell scripting problems"
date: 2005-04-08
forum: Programming Talk
---

### Post by theChauvinist on 2005-04-08
I've just started learning shell scripting, and am writing a script which installs all the programs I regularly use (after asking for the users consent), for use on fresh installs. So far I've only included GCC and Firefox.

However, at the moment it doesn't work how I want it to; it gives the spaces to type y or n before it actually asks the question. This is probably a dumb question, but hey, I've never programmed before  :-) .

```

#!/bin/bash

function aptget
{
   for app in gcc mozilla-firefox; do
     echo "Do you wish to install/update $app? [y/n]"
     read answer
        if [ "$answer" = "y" ]; then
          apt-get install $app
        else
          echo "you have chosen not to install $app"
      fi
   done
}

echo $(aptget)

```

---

### Post by Leif on 2005-04-08
Taking it out of the function works :

   for app in gcc mozilla-firefox; 
     do
     echo -n "Do you wish to install/update $app? [y/n]";
     read answer
        if [ "$answer" = "y" ]; then
          apt-get install $app
        else
          echo "you have chosen not to install $app"
	fi
   done

---

### Post by theChauvinist on 2005-04-08
Thanks a lot  :grin: . Thought it'd be something simple.

Do you know why it doesn't work as a function? (just out of curiosity)

---

### Post by Leif on 2005-04-08
No idea. I don't really do bash much, but I was just interested so I played around with it.

---

### Post by mendicant on 2005-04-08
What's the echo for?  This works fine, except for the echo.  Just change it to aptget.
My output is:

```
% source /tmp/blah
Do you wish to install/update gcc? [y/n]
y
would have done: apt-get install gcc
Do you wish to install/update mozilla-firefox? [y/n]
y
would have done: apt-get install mozilla-firefox
```

with the script:

cat /tmp/blah
```
#!/bin/bash

function aptget
{
   for app in gcc mozilla-firefox; do
     echo "Do you wish to install/update $app? [y/n]"
     read answer
        if [ "$answer" = "y" ]; then
          echo "would have done: apt-get install $app"
        else
          echo "you have chosen not to install $app"
      fi
   done
}

aptget

```

---

### Post by mendicant on 2005-04-08
You might also like "echo -n" to get rid of the newlines.

---

### Post by theChauvinist on 2005-04-09
Oh right, thanks, I'm not too sure why I put that echo there to be honest, I guess for some reason I thought you were meant to  :? .

I'll try that as soon as I can get back into Ubuntu.

Cheers!

---


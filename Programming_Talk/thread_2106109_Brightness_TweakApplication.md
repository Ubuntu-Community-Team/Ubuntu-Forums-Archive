---
title: "Brightness Tweak/Application"
date: 2013-01-18
forum: Programming Talk
---

### Post by eenofonn on 2013-01-18
Hi Everyone,

I've got a 27" Apple iMac mid 2011 with a core i5 2.7GHz quad core. One of the only problems that I can really find with it is the fact that you cannot change the brightness very easily nor does it do it automatically.  I was lucky enough to find a workaround:


```

xrandr --output LVDS --brightness x

```

Where x = a value within the range from 0.0-1.0

so I got to thinking and was wondering about one of two options

1 - Write a new application that does this easily and make it available to other users who may have the same problem.

2 - Find a way to tweak the builtin methods that attempt to adjust the brightness and make them use this method

So I started looking at how to write an application with Quickly (mainly because I've never writtien anything with a gui) to do this and hit a few roadblocks.

A - Surprise the language used is Python and I have no idea what I'm doing (so I can use google and attempt to find information)
B - I've never programmed in python before so I am having a terrible time trying to figure out how to run/call shell commands

So I guess what I'm getting at is, anyone want to help teach me python or show me a better method to creating gui applications with a perl backend etc... 

...or would someone like to help me write said application... 

...or anyone think that doing a system tweak to change the built-in controls is a good idea and know how I would get started on this?

---

### Post by MG&amp;TL on 2013-01-18
I was a little bored this morning (snow), so I coded this up for you quickly. You'll need to read through the code and replace the command I used, but the file is attached, and should run right away.

NB: the program doesn't work out what the initial brightness is. You could probably do that, but my guess is that nobody really cares too much.

IMHO Quickly is a waste of time, and no-one, especially not beginners, should try and use it. It also uses the sort of boilerplate, half-scripted approach that I despise. Hence this doesn't use Quickly, just a raw python file. If you want help writing something like an install script, I can do that too.

Works with both Python 2 and Python 3.

Happy coding!

---

### Post by eenofonn on 2013-01-18
> **MG&TL said:**
> I was a little bored this morning (snow), so I coded this up for you quickly. You'll need to read through the code and replace the command I used, but the file is attached, and should run right away.

NB: the program doesn't work out what the initial brightness is. You could probably do that, but my guess is that nobody really cares too much.

IMHO Quickly is a waste of time, and no-one, especially not beginners, should try and use it. It also uses the sort of boilerplate, half-scripted approach that I despise. Hence this doesn't use Quickly, just a raw python file. If you want help writing something like an install script, I can do that too.

Works with both Python 2 and Python 3.

Happy coding!

That is sick! I'm more familiar with perl and bash scripts so python just seems so Alien to me.  I see that it's printing the value with os.system I'm assuming I could just work with that to make the changes? are there any characters that have to be commented so python doesn't try to use them as part of a function? like in perl you have to comment out things like \ if you want to print it or whatnot.

---

### Post by DailyHealthcareguide on 2013-01-18
nice thanks

---

### Post by eenofonn on 2013-01-18
so I'm not sure what the issue is here but what I'm currently experiencing is that the interface for the input works fine but it lags I guess is the best way to describe what I'm seeing.  You run the slider one way or another and it's taking the input and adjusting the brightness but it's almost like it runs the command over and over and over very quickly.  I tried adding a sleep 0.5s && before issuing the command but that doesn't seem to help the issue it just makes it lag worse.  Any idea what I'm doing wrong here?

---

### Post by MG&amp;TL on 2013-01-18
> **eenofonn said:**
> That is sick! I'm more familiar with perl and bash scripts so python just seems so Alien to me.  I see that it's printing the value with os.system I'm assuming I could just work with that to make the changes? are there any characters that have to be commented so python doesn't try to use them as part of a function? like in perl you have to comment out things like \ if you want to print it or whatnot.

Yup, just change "echo" to that command you posted at first.  os.system() just spawns a shell to execute the command passed to it.

Quotes, and backslashes need to be escaped, but not much else, if I recall. 

Pleased you're happy. ;)

---

### Post by MG&amp;TL on 2013-01-18
> **eenofonn said:**
> so I'm not sure what the issue is here but what I'm currently experiencing is that the interface for the input works fine but it lags I guess is the best way to describe what I'm seeing.  You run the slider one way or another and it's taking the input and adjusting the brightness but it's almost like it runs the command over and over and over very quickly.  I tried adding a sleep 0.5s && before issuing the command but that doesn't seem to help the issue it just makes it lag worse.  Any idea what I'm doing wrong here?

Ah. Well, my (educated) guess is that the command causes lag for a set time period while it does its stuff. This isn't a major problem.

Solution 1: add a timeout to call the update function, instead of calling it every time the user moves the thing. This is what I've done.

Solution 2: add a button to apply the changes.

New file attached. :)

---

### Post by eenofonn on 2013-01-18
> **MG&TL said:**
> Ah. Well, my (educated) guess is that the command causes lag for a set time period while it does its stuff. This isn't a major problem.

Solution 1: add a timeout to call the update function, instead of calling it every time the user moves the thing. This is what I've done.

Solution 2: add a button to apply the changes.

New file attached. :)

cool thanks! I'm currently working on getting it to read the current brightness at start

---

### Post by MG&amp;TL on 2013-01-18
> **eenofonn said:**
> cool thanks! I'm currently working on getting it to read the current brightness at start

Cool. You might want to check this page: [http://stackoverflow.com/questions/6746126/how-to-store-the-return-value-of-os-system-that-it-has-printed-to-stdout-in-pyth](http://stackoverflow.com/questions/6746126/how-to-store-the-return-value-of-os-system-that-it-has-printed-to-stdout-in-pyth)

---

### Post by eenofonn on 2013-01-18
Ok so the main problem I'm having is creating a new variable to use as the original value in 

```

Gtk.Adjustment(x, 0, 100, 1, 1, 0)

```

the command I'm running in the shell to get the value is 

```

xrandr --current --verbose | grep Brightness | sed 's/[^0-9.]*//g'

```

and I'm pretty sure the value that I'm getting 0.0 - 1.0 needs to be multiplied by 100 to work in the field mentioned above, however the closest I can get is only printing these two lines, 
```

0.67
0

```

I got frustrated last night and don't have a copy of what I was trying to use but I'm pretty sure I was using 
```

subprocess.call(xrandr --current --verbose | grep Brightness | sed 's/[^0-9.]*//g')

```
Like I said, that's probably not exactly what I was using but I don't have my code in front of me to reference from.

Sorry but I'm a total python newb :(

---

### Post by MG&amp;TL on 2013-01-18
Perhaps this will help:

```
import subprocess

#Run the xrandr command within a shell, redirecting stdout.
result = subprocess.Popen("xrandr --current --verbose | grep Brightness | sed 's/[^0-9.]*//g'", shell=True, stdout=subprocess.PIPE)

#Print the first line of stdout, as a floating-point number 
print(float(result.stdout.read().split()[0]))

```

;)

---

### Post by eenofonn on 2013-01-18
> **MG&TL said:**
> Perhaps this will help:

```
import subprocess

#Run the xrandr command within a shell, redirecting stdout.
result = subprocess.Popen("xrandr --current --verbose | grep Brightness | sed 's/[^0-9.]*//g'", shell=True, stdout=subprocess.PIPE)

#Print the first line of stdout, as a floating-point number 
print(float(result.stdout.read().split()[0]))

```

;)
I think I might just love you lol

---

### Post by MG&amp;TL on 2013-01-18
> **eenofonn said:**
> I think I might just love you lol

:lolflag: That's a good one.

Let me know how you get on. :)

---

### Post by eenofonn on 2013-01-21
> **MG&TL said:**
> :lolflag: That's a good one.

Let me know how you get on. :)
I've had my kids all weekend and I've started looking at it but I think it's best if I look at some tutorials before I start messing around with python again.  Having a hard time wrapping my head around how to call variables or define them (whatever it's called) I will let you know when I get back to trying it


EDIT- I found what I was doing wrong!!! gedit wasn't showing the spacing correctly, I opened it up in nano and it was obvious what I was doing wrong.  I now have the completed code working for my machine but I want to be able to modify it for others who are using a different output so I'm going to find a way to grab that too :)

---

### Post by MG&amp;TL on 2013-01-21
> I've had my kids all weekend and I've started looking at it but I think it's best if I look at some tutorials before I start messing around with python again.  Having a hard time wrapping my head around how to call variables or define them (whatever it's called) I will let you know when I get back to trying it



Probably a good idea, but python is designed to be hackable for beginners, so you should be okay. :)

> EDIT- I found what I was doing wrong!!! gedit wasn't showing the spacing correctly, I opened it up in nano and it was obvious what I was doing wrong.  I now have the completed code working for my machine but I want to be able to modify it for others who are using a different output so I'm going to find a way to grab that too :)


Awesome! Yup, python's indents are a bit of a gotcha. Good luck with that!

---


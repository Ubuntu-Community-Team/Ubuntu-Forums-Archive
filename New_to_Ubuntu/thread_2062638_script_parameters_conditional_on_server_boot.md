---
title: "script parameters conditional on server boot"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by wimwam on 2012-09-25
I wish to create a script that is called on both boot and when a user logs in. As such, some of the parameters (specifically .config files) will be different depending on whether the machine is booting up or a user is logging in. Is there a means to capture this conditional in my init script?

I do NOT want to use Upstart, for reasons that i will not go into, so please don't suggest this.

So i guess my question is: 

is there a boolean, for example,  that i can capture which captures the state of the machine i.e. if bootingup = true then do .... else do ....

or alternatively how do i capture the error from logname, i.e. when there is no logname, or no one is logged into the system and use that as the boolean.

any ideas would be very welcome.

cheers,

wimwam

---

### Post by aromo on 2012-09-25
who --count returns the number of users currently logged in.  If it's 0, it means it's booting.  If it's > 0, that means it's somebody logging in.

How are you launching it at boot time if you're not using Upstart?

---

### Post by aromo on 2012-09-27
I was expecting, as a token of courtesy, to have my question replied after I took the time to think about the different alternatives to respond to the OP (evaluate different options,  research the right parameters and selecting the one I thought it was the easiest one, let alone the time I took to write the actual message).

For the 1st post, it would have been more polite to start up with a "Hi everybody, ..."  But I guess some people think their time is more important than others' or feel the rest of the world has to do what they want when they want without even saying "please".

I just wish my suggestion was useful and the OP could solve his/her problem.

---

### Post by wimwam on 2012-09-27
My apologies aromo,

I had every intention of replying. I am very appreciative of your answer and the trouble you took to make it. I have been trying to implement what you had suggested and was going to post a response once i could post an answer so that this thread could help people with a similar problem.

I am sorry that my response was not quick enough and thank you for your lesson in forum etiquette. I shall try and be less direct and more responsive in future.

---

### Post by HiImTye on 2012-09-28
the way that I would do it is just to provide the script with an argument, or not, to tell the script how to proceed. using this, you would launch the script at boot one way, and at login another. here are some examples:

** using an argument one method and none another:**
```
if [ -n "$1" ]; then
 we_are_booting
else
 we_are_not
fi
```with this, you would call the script at bootup *with* an argument:
```
 /path/to/script 1
```and at login *without*
```
/path/to/script
```**using one argument for one method and a different argument for another:**
```
if [ "$1" = "boot" ]; then
 we_are_booting
elif [ "$1" = "login" ]; then
 we_are_logging_in
fi
```with this, you would call the script at bootup with the '*boot*' argument
```
/path/to/script boot
```and at login with the '*login*' argument 
```
/path/to/script login
```


you could of course, use the number of users, or anything else to determine what to do, but this is how I would do it, to make it simple (KISS)

---

### Post by wimwam on 2012-10-01
Hi HilmTye,

Thanks for the response. this is a very good idea. i will implement this.

cheers,

---

### Post by wimwam on 2012-10-02
So, anybody who is interested, as to progress so far:

I have created a script which is referenced in start up (update-rc function) and via ~/.bash_login.

The script then loads a config file via a path set in the global environmental settings (/etc/environment) the value of which is overwritten by the ~/.bash_login file when a user logs in (export name=value).

this seems to work to some level. The problem that i am still encountering is that i am trying to get the script to use an array which is stored in /etc/init.d/script.config and ~/script.config (the effective file paths stored in the /etc/environment and ~/.bash_login files respectively.

i did not use the -b switch as suggested previously by HilmTye because i was concerned as to whether the rc implementation of the scripts at boot would allow for a switch? 

basically, i am still having problems but at the moment with the syntax for arrays in config files, they dont seem to like arrays and always exit with an unexpected "(" error. or can i store an array in the /etc/environment file.

any suggestions would be very much appreciated.

---


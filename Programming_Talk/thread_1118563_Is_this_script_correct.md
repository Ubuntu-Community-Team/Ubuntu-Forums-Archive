---
title: "Is this script correct?"
date: 2009-04-07
forum: Programming Talk
---

### Post by batharoy on 2009-04-07
Before we get started just remember I have never done this before, hence the topic title.
With my thirst for trying new things I think I've installed and un-installed 1/2 the Inrepid repo's.
By the time I got done there were over a 100 residuals needing to be cleaned.
So off to google I went and found this to autoclean them.
> sudo aptitude purge $(dpkg -l | grep '^rc' | awk '{print $2}')
I love you google! :P
Heck, I wont remember that command next week when I have to do this all over again.
I know, let's #!/bin/bash it, allow it to execute, and invoke it, ./purgerc
```
#!/bin/bash
sudo aptitude purge $(dpkg -l | grep '^rc' | awk '{print $2}')
```
HECK YA, works great. \\:D/ But wait, why cant I use the autoremove  command and do both jobs at once.
```
#!/bin/bash
sudo aptitude purge $(dpkg -l | grep '^rc' | awk '{print $2}')
sudo apt-get autoremove
```
Aw crap I broke it. :-k  Look again dummy. HELLOOOO autoremove before purge. #-o
At this point I've in/uninstalled the same 5 programs 10 more times to make sure this works as expected.
I gotta go pee, but I cant, have to sit here and push y+enter so the script will run. 
If I could only remember what that site was told me how to pass that flag and make it answer yes automagically.
FF history here I come, there it is. Yep, thats the page, scroll down, down, down. AHA, found it.
There it is, that elusive Y=YES flag "-y". #-o ](*,)
Oh ya, it also said always exit nicely.
```
#!/bin/bash
sudo apt-get autoremove -y
sudo aptitude purge -y $(dpkg -l | grep '^rc' | awk '{print $2}')
exit
```
Now I can go pee. Thanks for listening to my story.

Oh and um, is that code alright?
:p :p

---

### Post by batharoy on 2009-04-08
No reply yet.
Is the post too long?

---


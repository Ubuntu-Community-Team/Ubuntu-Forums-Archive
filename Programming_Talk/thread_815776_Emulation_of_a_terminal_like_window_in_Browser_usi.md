---
title: "Emulation of a terminal like window in Browser using HTML and a little javascript"
date: 2008-06-01
forum: Programming Talk
---

### Post by shoaibi on 2008-06-01
i read a posts at:
[http://www.dynamicdrive.com/forums/showthread.php?t=17450](http://www.dynamicdrive.com/forums/showthread.php?t=17450)
I must say very useful... I need a little help regarding that, if anyone can, please do...

I am developing a servlet, which would offer a terminal like window in browser to user, user will enter commands, this terminal like window will
block userinput, take the command, call the function
"execute_command(cmd)" with the cmd equal to the user input, take the
results from the execute_command command as String array, and show
them. It would have common shortcut keys like:

Up Arrow: displays previous command
Home: gets to the start of the command
End: takes to the end of command
Ctrl+C: stops the execution/fetching of results
etc

username and hostname will be stored in variables like user, hname;

Prompt would be like:
```

testuser@testsyste:# ping -c4 localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.078 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.118 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.079 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.082 ms

--- localhost ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.078/0.089/0.118/0.017 ms
testuser@testsyste:#

```

Please provide some idea on how should i do that. I dont know any
javascript, i know a little HTML, quite some java, and little bash if
that helps...

Thank you so much for reading the post.

---

### Post by Can+~ on 2008-06-02
Sounds very, VERY insecure, but interesting nonetheless.

Have you seen the ruby interactive shell?
[http://tryruby.hobix.com/](http://tryruby.hobix.com/)

Why not just use ssh?

---

### Post by Quikee on 2008-06-02
Sounds like you want to make something similar to [Ajaxterm]("http://antony.lesuisse.org/qweb/trac/wiki/AjaxTerm") or [Anyterm]("http://anyterm.org/").

---

### Post by shoaibi on 2008-06-02
Can+~:
nope, this terminal screen is protected with multiple login screens, and yes, at the backend i am using J2SSH, a java API for SSH to embed SSH into my servlet, 

Quickee:
(your avatar is nice, :P )
nope, thats more than what i want, but thanks... i want just a dummy frontend which does what i told in the first post...

If anyone is confused about what i want, i can re-state it...

oh, and i found this: [http://www.masswerk.at/termlib/](http://www.masswerk.at/termlib/)
i want to use this library such that after user input a line of text and presses enter, the javascript handler code sends this line of text to a function of java...
then reads the respones of that java function into an string array or string, and print it out to that dummy front end..

---

### Post by durand on 2008-06-02
Interesting idea, though I guess the other emulators are too heavy?

> Have you seen the ruby interactive shell?
[http://tryruby.hobix.com/](http://tryruby.hobix.com/)

That is seriously cool! Ruby seems to be a lot like python... 

> Sounds like you want to make something similar to Ajaxterm
Thats pretty awesome too :D

---

### Post by LaRoza on 2008-06-02
> **Can+~ said:**
> 
Have you seen the ruby interactive shell?
[http://tryruby.hobix.com/](http://tryruby.hobix.com/)


Python has one too: [http://www.mired.org/home/mwm/try_python/](http://www.mired.org/home/mwm/try_python/)

---

### Post by shoaibi on 2008-06-02
durand:
have you checked JSUnix? thats the most pretty thing around, i bet you will like it...

---

### Post by durand on 2008-06-02
> **shoaibi said:**
> durand:
have you checked JSUnix? thats the most pretty thing around, i bet you will like it...

Whoa, that looks awesome! Though I'm not really sure how to install it :o.

> Python has one too: [http://www.mired.org/home/mwm/try_python/](http://www.mired.org/home/mwm/try_python/)

Yeah, I think you, or someone else linked me that before. Its pretty good but the interesting bit about the Ruby one was that it had pretty cool tutorials.

---


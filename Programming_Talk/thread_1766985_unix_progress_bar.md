---
title: "unix progress bar"
date: 2011-05-25
forum: Programming Talk
---

### Post by Blackbug on 2011-05-25
i am having an application which takes some time to be installed. its a python script which install binaries over the desired locations.
i want to make a progress bar something like wget has ---->
 
i calculated the time it takes using TIME command, but this is too system specific thing. if any other user will install this at any slow/fast system time will be different.
 
how should i calculate this time? and also how should i implement this progress bar..

---

### Post by uzzen on 2011-05-25
Hello everybody!

This is my first post.
I was checking this forum regularly because of my interest in Ubuntu (Linux, in fact).
I subscribed to follow closely this thread: I have tried several times to implement something like a progress bar, but with no success.
I hope to find a solution here.

Best regards to everyone.

Wizard

---

### Post by Petrolea on 2011-05-25
I never needed something like this so I can't tell you exactly how to do it, but this should give you an idea on how to implement it in your code:

You must not set time first, that's wrong (as you said yourself already).

First, you would have to calculate the time that it should take (in wget it is calculated with - Size of file / downloading speed; remeber that is is never 100% accurate). 

If your script installs files over the internet, you would do the same thing: get the downloading speed and file size, then calculate the time it would take to download - for example: 400 kB file would need 1 second to download with 400 kB per second; 

Then you calculate how much has to be downloaded to fill the bar for 1% (assuming your bar has values from 1-100%). In this example, 1% would be 4 kB.

Make a loop that prints another character every time 4 kB has been downloaded. Example in pseudo code:

```

while (size of downloaded file does not equal full file size)
{
    if (n% is downloaded)
        print '-'

}

```

Hope this clears things up a bit.

---

### Post by Blackbug on 2011-05-25
well yes you right in terms of downloading files its a bit easy to find out on basis of network speed and size of file.
But, my scenario is a bit different, i am using a python script which install the lib (.so) files to various directories and it takes around 15 mins (approx on my system) to do so. But since this progress bar should not be system dependent I need some different approach.

---

### Post by slick666 on 2011-05-25
I've always used this utility.

[http://clpbar.sourceforge.net/]("http://clpbar.sourceforge.net/")

I don't think it's in the repos but its still being developed. I hope this helps.

---

### Post by Blackbug on 2011-05-25
it seems more for downloading purpose rather than installing
browsing code as of now, will post if anythin fruitful

---


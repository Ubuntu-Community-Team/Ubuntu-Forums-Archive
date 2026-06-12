---
title: "Malformed line in source list,  help please?"
date: 2015-04-12
forum: New to Ubuntu
---

### Post by wizrddreams on 2015-04-12
Hi there. I am new with using Ubuntu. I have had 14.04 installed on my Macbook as dual boot for a few months now. 

When I went to update packages earlier today I am getting this error:

```
sudo apt-get update
```

```
 
E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

```

Here is the relevant part of the sources.list

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
**deb [http://archive.canonical.com/](http://archive.canonical.com/) partner**
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) partner

Line 59 is the uncommented and bolded line.

What should I do to fix this?
I do not see any obvious errors. Is it the white-space?
And what is a likely reason that this happened?

---

### Post by yancek on 2015-04-12
Remove the comment (#) from the line below 59 and try it again.

---

### Post by papibe on 2015-04-12
Hi wizrddreams.

The name of the release is missing. My guess is, because of the other lines, that you are using trusty:
```
deb http://archive.canonical.com/ubuntu **[COLOR="#FF0000"]trusty[/COLOR]** partner
# deb-src http://archive.canonical.com/ubuntu [COLOR="#FF0000"]**trusty**[/COLOR] partner

```
To edit the file, open a terminal and run this:
```
sudo nano  /etc/apt/sources.list
```
Hope it helps. Let us know how that works out.
Regards.

---

### Post by wizrddreams on 2015-04-12
Hi, yancek. Thank you for the response. Before I noticed your response I went ahead and commented line 59 in the file. This worked. I ran sudo apt-get update and it went through.

I'm guessing you meant to say "comment line 59", right? Because there was no comment to remove.

---

### Post by wizrddreams on 2015-04-12
Hi, Papibe.
Excellent, thank you for the response.
Yes, I am using the trusty release.

I added "ubuntu trusty" into the sources.list file and all is working correctly now. 
Cheers.

---

### Post by sandyd on 2015-04-13
Hi, if you have found a solution, please mark this thread as solved via Thread Tools -> Mark thread as solved

Thanks!

---


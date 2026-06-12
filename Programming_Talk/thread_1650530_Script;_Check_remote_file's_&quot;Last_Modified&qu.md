---
title: "Script; Check remote file's &quot;Last Modified&quot;"
date: 2010-12-21
forum: Programming Talk
---

### Post by darkenvy6 on 2010-12-21
Now before anyone says anything, I have done a lot of web searching and can only find what I need in PHP, something that I cannot integrate with the rest of my script im writing.

I'm looking for the command that will give me the Last Modified date from a file from a website. If I go to properties in any web browser you can see the last modified date but how can I extract this using a script? (I think this is called the metadata of the file.)

Part two of my script writing adventure would be exporting the time with delimeters and rerunning the script with a +1 variable each time around. Pretend im trying to obtain the last modified info from "http://ubuntuforums.org/forumdisplay.php?f=xxxx" where f= is the variable that counts up starting at one. I could then have a file full of delimeters seperating the times of all the last-modifieds'

Does this make sense?

---

### Post by MadCow108 on 2010-12-22
```

curl --silent --head URL | grep "Last-Modified" || echo "no mod time"

```

---

### Post by darkenvy6 on 2010-12-23
> **MadCow108 said:**
> ```

curl --silent --head URL | grep "Last-Modified" || echo "no mod time"

```

Haha.... funny. But seriously is this a hard task to perform? I would imagine there would be a way to "delimiter" it out of the site.

---

### Post by MadCow108 on 2010-12-23
whats funny? This was a serious answer
Thats a way to get the modified from a site (when the site provides it)
```

curl --silent --head http://ubuntuforums.org/customavatars/avatar804725_1.gif | grep "Last-Modified" || echo "no mod time"
Last-Modified: Sat, 13 Jun 2009 23:52:19 GMT

```
many parts of sites, like the main forum url, don't provide this header as it makes no sense (page get updated on every user clicking on something)
but its useful for static data, e.g. pictures

---

### Post by darkenvy6 on 2010-12-23
Oh wow that did work XD. By looking at the script it looked like it wouldnt ever do anything but print "No Mod Time" so I thought you were messing with me :P.

Well now I am getting several responces not just the one we isolated:
```

[1] 2888
no mod time
xxxxxxx@yyyyyy:~$ HTTP/1.1 200 OK
Date: Thu, 23-Dec-2010 16:56:39 GMT
Server:
Content-type: image/gif
Cache-control: public, max-age=25920000
Expires: Wed, 19-Oct-2011 16:56:39 GMT
Last-modified: Thu, 16-Dec-2010 16:56:39 GMT
Connection: Close
Content-length: 8967

```So it works great but now I need another command to parse Last-modified out or a modification to the current line. Well.... almost runs great.... it prints the first two lines from above, returns to console then prints the rest and waits for something..... I think at this point I am still technicly at console though and am able to enter commands but then I am not able to retrieve what I need as it's technicly not an output :S

---


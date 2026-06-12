---
title: "C++, storing temporary files."
date: 2011-06-11
forum: Programming Talk
---

### Post by cgroza on 2011-06-11
Hello,

I am working on a program that is intended to be a sort of social client for Youtube.
The program must deal with video searches, downloads, previews and many more.

I want to offer the user a thumbnail of the selected video.
I have achieved the downloading of the image file, but now, a problem arises.

I need a place to store these images and to delete them after.

So far I have 2 approaches to this.

One of them is to store them in the temporary directory, but I have not found a cross platform way to do this yet.

Another one is to manage the file deletion myself, but I feel this is a too big burden on me and in the case of a crash, would leave garbage on the system.

I am here to ask the advice about other possible approaches or a way to get the temporary folder in a portable way.

The boost library seems to offer something, but I did not find the required function. 

Thank you.

---

### Post by simeon87 on 2011-06-11
Applications often create a directory called .bla where bla is the application name. These directories are used to store application configuration files, user preferences and other data. You could store your image files in there as well and delete them when the program finishes.

> **cgroza said:**
> Another one is to manage the file deletion myself, but I feel this is a too big burden on me and in the case of a crash, would leave garbage on the system.

Not necessarily, you could delete them the next time the application launches (i.e., check for image files, delete them if needed).

---

### Post by cgroza on 2011-06-11
> **simeon87 said:**
> Applications often create a directory called .bla where bla is the application name. These directories are used to store application configuration files, user preferences and other data. You could store your image files in there as well and delete them when the program finishes.



Not necessarily, you could delete them the next time the application launches (i.e., check for image files, delete them if needed).

This seems the best approach. Thank you.
I am still open to other suggestions.

---

### Post by BkkBonanza on 2011-06-11
Is there a reason not to use the [tmpfile]("http://www.cplusplus.com/reference/clibrary/cstdio/tmpfile/")() function defined in stdio. It creates and opens tmp file and it will delete it when closed. Or [tmpnam]("http://www.cplusplus.com/reference/clibrary/cstdio/tmpnam/")() if you need more control. 

I haven't needed to use this but I'd expect it works on all platforms - haven't checked that.

---

### Post by cgroza on 2011-06-11
> **BkkBonanza said:**
> Is there a reason not to use the [tmpfile]("http://www.cplusplus.com/reference/clibrary/cstdio/tmpfile/")() function defined in stdio. It creates and opens tmp file and it will delete it when closed. Or [tmpnam]("http://www.cplusplus.com/reference/clibrary/cstdio/tmpnam/")() if you need more control. 

I haven't needed to use this but I'd expect it works on all platforms - haven't checked that.
That seems to force me to download the same file multiple times if the same entry is selected 2 times. Because the temp file is deleted when it is destroyed, it would require me to keep many of them open while I need them, which is during all the time the application runs.

---

### Post by r-senior on 2011-06-11
Are the cache files potentially reusable from session to session?

What about using the same approach as a browser cache? Let it grow up to a defined size, then delete the oldest when you want to create new ones above the size limit? Or you could take the same approach as the trash and delete based on age with no strict size limit?

Maybe you'd then need a "clear cache" option?

---

### Post by cgroza on 2011-06-11
> **r-senior said:**
> Are the cache files potentially reusable from session to session?

What about using the same approach as a browser cache? Let it grow up to a defined size, then delete the oldest when you want to create new ones above the size limit? Or you could take the same approach as the trash and delete based on age with no strict size limit?

Maybe you'd then need a "clear cache" option?
Yes, but what are the chances the user will have the same range of videos from session to session and that he will select the one I have a cached file for?

---

### Post by r-senior on 2011-06-11
> **cgroza said:**
> Yes, but what are the chances the user will have the same range of videos from session to session and that he will select the one I have a cached file for?
It's your application and you'd know better than I would, but, other than simply watching something again, could someone download a video, watch part of it and come back to it later perhaps?

---

### Post by cgroza on 2011-06-11
> **r-senior said:**
> It's your application and you'd know better than I would, but, other than simply watching something again, could someone download a video, watch part of it and come back to it later perhaps?
Maybe, but then the user will not need a preview. The user already saw it or watched some of it.

---

### Post by BkkBonanza on 2011-06-11
> **cgroza said:**
> That seems to force me to download the same file multiple times if the same entry is selected 2 times. Because the temp file is deleted when it is destroyed, it would require me to keep many of them open while I need them, which is during all the time the application runs.

As mentioned, the tmpnam() function gives you more control as it doesn't force a delete when closed. You just use it to generate a unique name and then pass that as filename to open.

Another way would be to generate the filename as a hash of the original video url - that way the same url would always map to the same filename. There are some very simple/fast [hash]("http://en.wikipedia.org/wiki/MurmurHash") [functions]("http://en.wikipedia.org/wiki/Fowler-Noll-Vo_hash_function") that would work for that and it would fit into a cache scheme better too. eg. if you generate the filename and it already exists then you know it's been downloaded already, or if length is not correct then you know a resume d/l is needed.

(This is probably a better ref for [MurmurHash3]("http://code.google.com/p/smhasher/wiki/MurmurHash3"))

---

### Post by cgroza on 2011-06-11
> **BkkBonanza said:**
> As mentioned, the tmpnam() function gives you more control as it doesn't force a delete when closed. You just use it to generate a unique name and then pass that as filename to open.

Another way would be to generate the filename as a hash of the original video url - that way the same url would always map to the same filename. There are some very simple/fast [hash]("http://en.wikipedia.org/wiki/MurmurHash") [functions]("http://en.wikipedia.org/wiki/Fowler-Noll-Vo_hash_function") that would work for that and it would fit into a cache scheme better too. eg. if you generate the filename and it already exists then you know it's been downloaded already, or if length is not correct then you know a resume d/l is needed.
This could be exactly what I need. Thank you. I already use the youtube video ID as a unique name so I do not need a hash.

---

### Post by cgroza on 2011-06-11
Just found out that the temp folder can be obtained with **P_tmpdir **from[B] stdio.h.
[/B]

---

### Post by BkkBonanza on 2011-06-11
> **cgroza said:**
> This could be exactly what I need. Thank you. I already use the youtube video ID as a unique name so I do not need a hash.

Just prefix the video id with something unique to your app. eg. groza

And if you want, when you start up remove anything, groza* if you want to be sure the tmp files are wiped.

---

### Post by SledgeHammer_999 on 2011-06-11
Also if you're using a GUI toolkit like Gtk, then there are helper functions to find the Temp folder on every platform.

---

### Post by cgroza on 2011-06-11
> **SledgeHammer_999 said:**
> Also if you're using a GUI toolkit like Gtk, then there are helper functions to find the Temp folder on every platform.
I am using wxWidgets. I will try to find that helper function.

---

### Post by cgroza on 2011-06-11
> **BkkBonanza said:**
> Just prefix the video id with something unique to your app. eg. groza

And if you want, when you start up remove anything, groza* if you want to be sure the tmp files are wiped.
Thanks for the tip.

---

### Post by cgroza on 2011-06-11
> **SledgeHammer_999 said:**
> Also if you're using a GUI toolkit like Gtk, then there are helper functions to find the Temp folder on every platform.
Got it! 
**wxStandardPaths::GetTempDir()**

---


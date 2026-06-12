---
title: "Wget &quot;since it should be rejected&quot; help"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by FLCL on 2011-10-10
I'm trying to use wget download all the files(images) linked in a given directory

**Example:** [http://imgur.com/r/fitness](http://imgur.com/r/fitness)

The images are not actually inside this directory but only displayed. 
```
**Example:** imgur.com/r/fitness/picture 
``` you can view it the image and save it but if you tack on extension .jpg at the end, it's not there. If you view the actual image url it's in ```
i.imgur.com/picture.jpg
```

However these links are in the index.html so using -r and -l1 should follow those links right? Apparently not

It stops immediately, providing: ```
Removing imgur.com/r/fitness since it should be rejected.
```

My string is ```
wget -r -l1 -A.jpg,.gif -I /i.imgur.com, /fitness -X /blog,/tools http://imgur.com/r/fitness
```

Can someone **please** help? I'm struggling with this and cannot seem to get this. Is it even possible? Thanks!

---

### Post by An Sanct on 2011-10-11
Your code seems totally fine to me.

But! :)

If you take a look at this page
[http://imgur.com/r/fitness/gRah0](http://imgur.com/r/fitness/gRah0)
You see 6 small images on the left side. After inspection of the HTML code, you only see 6 '.jpg' strings and they are _not_ links (they are '<img src=' ....)

The big picture is a link tho, here:
[http://imgur.com/download/gRah0/Four%20weeks%20on%20LeanGains...%20this%20shit%20works](http://imgur.com/download/gRah0/Four%20weeks%20on%20LeanGains...%20this%20shit%20works).

Notice, that the extension is ".", so there lies your problem :)

PS. Image hosting sites don't like mass downloaders, so they protect them self.

---

### Post by Lisiano on 2011-10-11
Try separating -A and the extensions, also try without the dots.
Try adding html as an extension since it will ignore it and not crawl it since you told it not to download it.

---

### Post by FLCL on 2011-10-12
Hm, i've tried what you mentioned Lisiano but no luck. I'm starting to think wget isn't able to perform the task. Even though the images are embedded in src tags, it should be able to follow the location and grab the image (so I would imagine). This is what ends up happening:

```
mikado@box:~$ wget -r -l1 -A html,jpg,gif -I /i.imgur.com, /fitness -X /blog,/tools http://imgur.com/r/fitness
/fitness: Scheme missing.
--2011-10-12 18:32:13--  http://imgur.com/r/fitness
Resolving imgur.com... 173.231.140.218, 173.231.140.219
Connecting to imgur.com|173.231.140.218|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `imgur.com/r/fitness'

    [ <=>                                   ] 22,812      --.-K/s   in 0.1s    

2011-10-12 18:32:14 (172 KB/s) - `imgur.com/r/fitness' saved [22812]

Loading robots.txt; please ignore errors.
--2011-10-12 18:32:14--  http://imgur.com/robots.txt
Connecting to imgur.com|173.231.140.218|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1 [text/plain]
Saving to: `imgur.com/robots.txt'

100%[======================================>] 1           --.-K/s   in 0s      

2011-10-12 18:32:14 (97.4 KB/s) - `imgur.com/robots.txt' saved [1/1]

Removing imgur.com/r/fitness since it should be rejected.

--2011-10-12 18:32:14--  http://imgur.com/gallery/
Connecting to imgur.com|173.231.140.218|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `imgur.com/gallery/index.html'

    [  <=>                                  ] 67,955       175K/s   in 0.4s    

2011-10-12 18:32:14 (175 KB/s) - `imgur.com/gallery/index.html' saved [67955]

--2011-10-12 18:32:14--  http://imgur.com/
Connecting to imgur.com|173.231.140.218|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `imgur.com/index.html'

    [ <=>                                   ] 13,613      --.-K/s   in 0.09s   

2011-10-12 18:32:15 (141 KB/s) - `imgur.com/index.html' saved [13613]

--2011-10-12 18:32:15--  http://imgur.com/images/imgur-small.gif
Connecting to imgur.com|173.231.140.218|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1087 (1.1K) [image/gif]
Saving to: `imgur.com/images/imgur-small.gif'

100%[======================================>] 1,087       --.-K/s   in 0s      

2011-10-12 18:32:15 (188 MB/s) - `imgur.com/images/imgur-small.gif' saved [1087/1087]

--2011-10-12 18:32:15--  http://imgur.com/images/album_loader.gif
Connecting to imgur.com|173.231.140.218|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6366 (6.2K) [image/gif]
Saving to: `imgur.com/images/album_loader.gif'

100%[======================================>] 6,366       --.-K/s   in 0s      

2011-10-12 18:32:15 (334 MB/s) - `imgur.com/images/album_loader.gif' saved [6366/6366]

--2011-10-12 18:32:15--  http://imgur.com/stats/
Connecting to imgur.com|173.231.140.218|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `imgur.com/stats/index.html'

    [ <=>                                   ] 13,982      --.-K/s   in 0.09s   

2011-10-12 18:32:15 (146 KB/s) - `imgur.com/stats/index.html' saved [13982]

FINISHED --2011-10-12 18:32:15--

```

---

### Post by Lisiano on 2011-10-13
Just noticed that the file (fitness) does not have a extension, so it can't be applied to the -A regex, we need to tell wget to add a .html extension if it sees that the file contains html stuff, just add this argument to wget. I just tested the line you used with the argument added. Worked.
```
-E
```
This is how it should look like
```
wget -r -l1 -p -A html,jpg,gif -I /i.imgur.com, /fitness -X /blog,/tools -E http://imgur.com/r/fitness
```Notice the -p, it's so that everything needed to display the image is downloaded but since you specify -A, it will only download files that pass that -A argument, or else it might not download stuff on the last page.

---

### Post by sadaruwan12 on 2011-10-13
Well, If you're using firefox use the downthemall addon it can do a mass download of your files images what in a single click.

Right click on the web page and give download page images it'll do the rest with out any problem.

---

### Post by FLCL on 2011-10-13
Awesome \\:D/ learned something new. And sadar, I did look at that addon, it only downlaoded the thumbnails in imgur's case. Probably because the way their system is set up. 
Looks like the images are in an entirely different directory but get called on somehow. Could be completely wrong though, I'm no expert lol 

Thanks Lisiano!

---


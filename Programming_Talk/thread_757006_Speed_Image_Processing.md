---
title: "Speed Image Processing"
date: 2008-04-16
forum: Programming Talk
---

### Post by nonaguy on 2008-04-16
My company wants a web application for local intranet use to view some 70,000 high quality tiffs (these are imaged historical documents). Our plan is to use php with imagemagick to load the images in memory, convert them, and echo out the results without touching the original tiffs. The problem here is that this is somewhat sluggish, averaging out at about 7 seconds an image. Are there any programs out there that specialize in speed processing? We would even consider speed over quality in this case (provided quality dip is not TOO horrible). Any help would be appreciated. 
Also, here is the php we are using:

<?php
$resolution=$_GET["res"];
$presize=($resolution*2);
$photo="test.tif";
$cmd = "convert \"$photo\" -scale 50% -strip -unsharp 0.2x0.6+1.0 -quality 87 JPG:-";
header("Content-type: image/jpeg");
passthru($cmd, $retval);
?>

---

### Post by lnostdal on 2008-04-16
```

CL-USER> (float (/ (* 7 70000) 60 60 24))
5.671296

```

so that's about 6 days or 136.1 hours to convert all the 70,000 images to jpg format .. ie; convert them beforehand

---

### Post by nanotube on 2008-04-16
another alternative: don't waste time converting tiff to jpeg - just view them directly in the browser with a tiff plugin:
[http://tiff-plugin.sourceforge.net/](http://tiff-plugin.sourceforge.net/)

---

### Post by CptPicard on 2008-04-16
Either convert beforehand or... cache the result. You'll get all of them converted over time. :)

You don't even need to alter any code if you do something like running Squid as a front-side cache proxy...

---

### Post by nonaguy on 2008-04-16
70,000 images is our test load, the project scope is well over 1,000,000 images. We do not want a permanent conversion, due to a long variety of reasons. We have the tiffs in an uncompressed 70 Mb per file, on average, for archival purposes.  If any errors are discovered in the source images, we do not want to have to go back through and reconvert or recache it somehow. The bandwidth to transfer unconverted images using the tiff browser plugin would be excessive, as people will flip through these like pages in a book. We want to real time process (which we have already figured out how to do); our concern at this point is to make the process as fast as possible.  Whether this means replacing imagemagik or optimizing it in some way (we have already asked how on their forums with little success) is what we are trying to figure out.

---

### Post by lnostdal on 2008-04-16
> due to a long variety of reasons. 
like -- it would be too easy?

> . If any errors are discovered in the source images, we do not want to have to go back through and reconvert or recache it somehow.

this don't make no sense .. if there is an error, log it and move on to the next image .. you don't restart the entire process .. lol ...   no, you log it then you go back and deal with the "problem-images" semi-manually later

---

### Post by lnostdal on 2008-04-16
what about these multipass type jpg files (or whatever they are called) .. the type where the image show up at once, but with quite low quality .. then gradually gets better over time as more data is downloaded

what about slicing the original up in pieces (edit: not necessarily as multiple files, no .....)  .. you only convert a cropped piece of the original file ...

etc. .. many possibilities really

edit:
..i don't know whether these things are possible in your case though..

---

### Post by mssever on 2008-04-16
> **lnostdal said:**
> this don't make no sense .. if there is an error, log it and move on to the next image .. you don't restart the entire process .. lol ...   no, you log it then you go back and deal with the "problem-images" semi-manually later

I think the OP is referring to problems in the image *content*, not the file itself (e.g., an incorrect caption embedded in the image).

@OP:
Given the size of your source files, you'll probably have to upgrade your hardware if you want significant speed imporvements for each individual image. But don't write caching off. You can cache the image along with a timestamp. If the modification date of the original is later than the cache or that particular file isn't cached yet, then generate a cache. Otherwise, simply serve up the cache.

You could even write a little program to hunt for stale caches and update them behind the scenes. You might run it as a cron job, or you might run it as a daemon that continually watches for changes.

---

### Post by LaRoza on 2008-04-16
> **lnostdal said:**
> what about these multipass type jpg files (or whatever they are called) .. the type where the image show up at once, but with quite low quality .. then gradually gets better over time as more data is downloaded


Interlaced.

---

### Post by pmasiar on 2008-04-16
We have similar problem: we have many huge tiff files, which obviously take forever to process and bring up in browser. Some idiot suggested using jpeg compression, but our boss said he can see the difference between jpeg and tiff (he is **really** smart). We are thinking about getting really big fast expensive server with really fat internet connection to speed up downloading the images, but it will cost a lot. Should we consider that idiot's advice? Compressed files are obviously so much inferior as to be unusable for smart people like our boss? And disk space for processed compressed files is cheap, but nobody is willing to maintain 40 lines script creating compressed mirror. We are into big-scale enterprise class solutions, no trivial cheap solutions could satisfy our really smart boss. What we should do?

:twisted:

---

### Post by mssever on 2008-04-16
Here's another thought: I haven't done much with TIFF files, but I don't recall that they use much compression. PNGs might be a reasonable compromise, since they use lossless compression. Plus, you can index them to an optimal pallette if that works for your data, saving more space.

---

### Post by nanotube on 2008-04-16
> **nonaguy said:**
> 70,000 images is our test load, the project scope is well over 1,000,000 images. We do not want a permanent conversion, due to a long variety of reasons. We have the tiffs in an uncompressed 70 Mb per file, on average, for archival purposes.  If any errors are discovered in the source images, we do not want to have to go back through and reconvert or recache it somehow. The bandwidth to transfer unconverted images using the tiff browser plugin would be excessive, as people will flip through these like pages in a book. We want to real time process (which we have already figured out how to do); our concern at this point is to make the process as fast as possible.  Whether this means replacing imagemagik or optimizing it in some way (we have already asked how on their forums with little success) is what we are trying to figure out.

heh wow, 70 TB of images... you really /should/ consider caching the jpeg conversions, and updating the jpegs only if the originals change.

---

### Post by nonaguy on 2008-04-24
Hey guys, sorry for the delay in my response, been REALLY busy at work.


> **mssever said:**
> I think the OP is referring to problems in the image *content*, not the file itself (e.g., an incorrect caption embedded in the image).

@OP:
Given the size of your source files, you'll probably have to upgrade your hardware if you want significant speed imporvements for each individual image. But don't write caching off. You can cache the image along with a timestamp. If the modification date of the original is later than the cache or that particular file isn't cached yet, then generate a cache. Otherwise, simply serve up the cache.

You could even write a little program to hunt for stale caches and update them behind the scenes. You might run it as a cron job, or you might run it as a daemon that continually watches for changes.

That's exactly what I meant, in regards to image content. Now this is an interesting idea, and going back to CptPicard's reply, would Squid (or another prebuilt package) be able to handle this type of caching or would we need to implement it in the php?

> **LaRoza said:**
> Interlaced.

Are you referring to JPEG2000, or something different?

> **pmasiar said:**
> We have similar problem: we have many huge tiff files, which obviously take forever to process and bring up in browser. Some idiot suggested using jpeg compression, but our boss said he can see the difference between jpeg and tiff (he is **really** smart). We are thinking about getting really big fast expensive server with really fat internet connection to speed up downloading the images, but it will cost a lot. Should we consider that idiot's advice? Compressed files are obviously so much inferior as to be unusable for smart people like our boss? And disk space for processed compressed files is cheap, but nobody is willing to maintain 40 lines script creating compressed mirror. We are into big-scale enterprise class solutions, no trivial cheap solutions could satisfy our really smart boss. What we should do?

:twisted:

If pan and zoom functions are appropriate, look into IIPImage and conversion to lossless PTIF; we used this solution for another of our record sets with 200 MB TIFFS (note that this will not give the same file size as a file compressed with JPEG).


> **mssever said:**
> Here's another thought: I haven't done much with TIFF files, but I don't recall that they use much compression. PNGs might be a reasonable compromise, since they use lossless compression. Plus, you can index them to an optimal pallette if that works for your data, saving more space.

We will look into this, as well as any other *lossless* formats (we are investigating PNG and JPEG2000). Any other format suggesstions?

---

### Post by mssever on 2008-04-24
> **nonaguy said:**
> That's exactly what I meant, in regards to image content. Now this is an interesting idea, and going back to CptPicard's reply, would Squid (or another prebuilt package) be able to handle this type of caching or would we need to implement it in the php?
There's probably software out there to handle such caching. I don't really know what's out there since I haven't had to bother with caching for my projects. I'm sure that wouldn't be too hard to research. Given that CptPicard suggested Squid, that would be worth looking into.

---

### Post by CptPicard on 2008-04-24
You know if running a compressed mirror is an option, running a simple makefile over and over again will reprocess only those originals that have changed... make has a lot of other uses than running compilers :p

---

### Post by nonaguy on 2008-04-25
> **CptPicard said:**
> You know if running a compressed mirror is an option, running a simple makefile over and over again will reprocess only those originals that have changed... make has a lot of other uses than running compilers :p

We feel that a compressed mirror is a step in the wrong direction. We experimented with JPEG-2000, and while it reduced file size by about half, it also tripled processing time. We also experimented with PNGS, and while it reduced file size by a third, it slightly increased processing time (which we are trying to shave by seconds, or even milliseconds if possible).

---

### Post by mssever on 2008-04-25
> **nonaguy said:**
> We feel that a compressed mirror is a step in the wrong direction. We experimented with JPEG-2000, and while it reduced file size by about half, it also tripled processing time. We also experimented with PNGS, and while it reduced file size by a third, it slightly increased processing time (which we are trying to shave by seconds, or even milliseconds if possible).

But if you're caching, then processing time doesn't matter a whole lot, because you only have to process new images and images that you change. So you're dealing with the time to process a single image, not the time to process all 1 million images in your archive.

---

### Post by CptPicard on 2008-04-25
And the Squid proxy sort of creates exactly the same kind of mirror, only this time in response to user request. Cost in space and aggregate computation time is the same, only the mechanism is different. Think of that Makefile (or Scons-file) solution I suggested, once you've got them all converted into the mirror, you only pay in processing time every time an image changes (you know how make works?).

---

### Post by winch on 2008-04-25
> **CptPicard said:**
> And the Squid proxy sort of creates exactly the same kind of mirror, only this time in response to user request.

I think the difference in response time between a cache hit and miss could be a bit of a problem here. Users are "flipping through images like pages in a book". Their experience is going to be much better if all images load in a quick and consistent amount of time. Applications that randomly go slow can be very annoying.

---

### Post by evymetal on 2008-04-25
pmasiar: That's hilarious.

OP:
ImageMagik is fairly fast - you're not going to get a huge speed up with anything else short of writing your own custom code in assembly (and it's still not going to be as fast as you want it).

I don't know your full use case, but I would assume that not all images will get viewed equally as many times. I would definitely say you should either convert them to jpeg in advance, or on the fly when the user views it.

If you *need* to do it on the fly (I can't imagine why you would, though), then I would put a reverse proxy on the front - using Squid or Apache (I had bad experiences with squid but that was probably almost 10 years ago now, and it's widely used).

Set the time to live on the proxy to be a relatively short time and pre-converted images will be removed, allowing modifications to the original to filter through the system fast.

If the time to convert a single image is still too slow, and you are using a flipbook style then you can pre-convert the linked images to jpg in advance, when you serve the links to them. Keep then cached on the backend server for an hour or so (or until they get requested by the proxy), and then delete them.


Still - It would be far easier to convert the images to jpg right up front!

BTW I wouldn't suggest JPG2000

---

### Post by mssever on 2008-04-25
> **evymetal said:**
> Keep then cached on the backend server for an hour or so (or until they get requested by the proxy), and then delete them.

Still - It would be far easier to convert the images to jpg right up front!

Instead of caching them for an hour, just cache them until they change. No need to waste cycles generating identical caches.

Also, remember that the OP said that he/she needed to maintain a lossless format. JPG is lossy, and is really only acceptable for photographs (their intended use). For other kinds of data, the quality degrades very quickly.

---

### Post by evymetal on 2008-04-26
> **mssever said:**
> 
Also, remember that the OP said that he/she needed to maintain a lossless format. JPG is lossy, and is really only acceptable for photographs (their intended use). For other kinds of data, the quality degrades very quickly.

The OP said 
> We would even consider speed over quality in this case (provided quality dip is not TOO horrible)
JPEG with highest quality is good enough for most uses - or use PNG. I still don't suggest JPEG 2000 - there are too many potential legal issues (think what happened with .gif)


Agreed with the proxying setting - so long as you can serve your own last-modified date (I'm not a PHP guy, I'm not sure if you have access to that header or if you have to leave it to Apache). If that's a problem you could hack together a specialist image web server in Python (It's almost as easy as writing a cgi program) - and then you have complete control of the headers you send to the proxy.

If the OP is worried about milliseconds then I would suggest writing your own server anyway - it's moderately faster than running as a cgi (even with [e.g.] modperl), and you can process the next images after you have finished sending the page to the user - but not that many people really need milliseconds - most of a user's load time is spent rendering the page in their browser and doing dns/routing these days.


Not sure what the OP's experience is - but I guess the main thing to take away is that when you start to try to convert and serve 70 TB of data live and you care about milliseconds things start getting fairly complicated!

Here are some more problems:

- you're going to get loads of HD failures, so you'd better have a reliable storage solution.

- if you serve it from a network share then you should convert it direct on that server - pumping out 70Mb of data to another server before converting it to JPG is just pointless and will block your network if you have significant load

- if the data is spread over multiple hard disks (I hope it is) then you're going to have to worry about the time it takes to get the disks up to speed if you let them sleep (or pay a lot more in power costs if you don't)

- don't forget seek time - 70Mb files are going to get fragmented unless you use a write-once system. 

- if it takes about 7 seconds to convert an image then you really need to worry about this. If you've got 4 cores/processors on each server then each server can only handle requests for 4 different (un-cached) images every seven seconds. If this sounds fine, check what your peak load is going to be - one person could open four different images in four tabs, and then you're screwed (think about when googlebot comes to crawl!).


Sounds like a fun problem, though (I love problems like this - each large application is so different)

---

### Post by nonaguy on 2008-05-02
Thank you to everyone who responded to this. After much testing and experimentation, we have determined that we cannot process the images any faster then we currently are. The best speed we have gotten was 4 seconds, using the passthru command on PHP with Imagemagick, with it served out on Lighttpd. There are other ways to get it faster, but the images were too dodgy. We are going to try a cacheing solution, as suggested by several people, and possibly a hardware upgrade. Again, thanks everyone.

---

### Post by Daveski on 2008-05-02
> **pmasiar said:**
> Should we consider that idiot's advice? Compressed files are obviously so much inferior as to be unusable for smart people like our boss? 

Depends on the content of the images, but jpeg with minimum compression should be almost undetectable and still saves space (and transmission time).

---

### Post by CptPicard on 2008-05-02
Unless it's something like medical imagery where standards are very strict... you don't want to get diagnosed with brain cancer because there's a jpeg artifact in the scan...

---


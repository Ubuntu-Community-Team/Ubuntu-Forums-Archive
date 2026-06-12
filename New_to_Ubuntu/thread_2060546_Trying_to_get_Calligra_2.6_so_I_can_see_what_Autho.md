---
title: "Trying to get Calligra 2.6 so I can see what Author is like?"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-09-20
jacky@jacky-Aspire-6930G:~$ [url "git://anongit.kde.org/"]
No command '[url' found, did you mean:
 Command 'curl' from package 'curl' (main)
[url: command not found
jacky@jacky-Aspire-6930G:~$     insteadOf = kde:
insteadOf: command not found
jacky@jacky-Aspire-6930G:~$ [url "ssh://git@git.kde.org/"]
No command '[url' found, did you mean:
 Command 'curl' from package 'curl' (main)
[url: command not found
jacky@jacky-Aspire-6930G:~$     pushInsteadOf = kde:wget -c http://anongit.kde.org/calligra/calligra-latest.tar.gz
pushInsteadOf: command not found
jacky@jacky-Aspire-6930G:~$ wget -c http://anongit.kde.org/calligra/calligra-latest.tar.gz
--2012-09-20 11:50:13--  http://anongit.kde.org/calligra/calligra-latest.tar.gz
Resolving anongit.kde.org (anongit.kde.org)... 31.216.41.69, 2a01:4f8:130:4ffd:1:cae:dee:ee05
Connecting to anongit.kde.org (anongit.kde.org)|31.216.41.69|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: /calligra/calligra_20120919041339_sha1-1910dc42144c28268b63b75257e974049acc78be.tar.gz [following]
--2012-09-20 11:50:14--  http://anongit.kde.org/calligra/calligra_20120919041339_sha1-1910dc42144c28268b63b75257e974049acc78be.tar.gz
Reusing existing connection to anongit.kde.org:80.
HTTP request sent, awaiting response... 200 OK
Length: 541575126 (516M) [text/plain]
Saving to: `calligra-latest.tar.gz'

67% [=========================>             ] 365,906,800 --.-K/s  eta 26m 39s 
67% [=========================>             ] 365,906,800 --.-K/s   in 61m 14s 

2012-09-20 12:51:28 (97.3 KB/s) - Read error at byte 365906800/541575126 (Connection timed out). Retrying.

--2012-09-20 12:51:29--  (try: 2)  http://anongit.kde.org/calligra/calligra_20120919041339_sha1-1910dc42144c28268b63b75257e974049acc78be.tar.gz
Connecting to anongit.kde.org (anongit.kde.org)|31.216.41.69|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 541575126 (516M), 175668326 (168M) remaining [text/plain]
Saving to: `calligra-latest.tar.gz'

100%[++++++++++++++++++++++++++============>] 541,575,126  250K/s   in 23m 7s  

2012-09-20 13:14:37 (124 KB/s) - `calligra-latest.tar.gz' saved [541575126/541575126]

jacky@jacky-Aspire-6930G:~$ 
jacky@jacky-Aspire-6930G:~$ $ ./initrepo.sh
$: command not found
jacky@jacky-Aspire-6930G:~$ ^C
jacky@jacky-Aspire-6930G:~$ tar -zxvf {file.tar.gz}
tar (child): {file.tar.gz}: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
jacky@jacky-Aspire-6930G:~$ tar -zxvf backup.tar.gz
tar (child): backup.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
jacky@jacky-Aspire-6930G:~$ 

So you can see where I got. I think the problem is I don't really know how to unpack the files.

Here is where I was trying to get it from.

http://community.kde.org/Calligra/Building#Get_the_source_code_for_the_development_version

Using Ubuntu 12.4

I don't think this is a stable release yet but I am rather keen to try it out. I may of course be barking up the wrong tree but now I downloaded all that......I am not even sure it is a release as such? Anyway  be interesting to see how far they are on if anyone can figure that out and tell me and the release itself is due in December.

---

### Post by vasa1 on 2012-09-20
Why don't you use the GUI? Open your file manager (Nautilus?). Change to the folder holding the tar file, right-click on it and choose "extract here".

---

### Post by Jackalyn on 2012-09-20
> **vasa1 said:**
> Why don't you use the GUI? Open your file manager (Nautilus?). Change to the folder holding the tar file, right-click on it and choose "extract here".
  That is what I wanted to do but I cannot find the file!!!!

---

### Post by Sealbhach on 2012-09-20
It should be in your /home folder, since that is the folder you ran wget from.

If you have trouble finding something, the "locate" command is useful. First, update the database:

```
sudo updatedb
```

Then run locate, in this case you're looking for "calligra-latest"

```
locate calligra-latest
```

It should find you the right folder location instantly.

You could also install [recoll]("http://www.lesbonscomptes.com/recoll/features.html"), which is a good file indexer and is simple to use.  It not only lets you search for filenames, but also the text within files.

I think KDE has something like that running as standard, not sure if Gnome does, but I see recoll has now got a [Unity lens]("http://www.webupd8.org/2012/03/recoll-lens-full-text-search-unity-lens.html").

.

---

### Post by Jackalyn on 2012-09-21
> **Sealbhach said:**
> It should be in your /home folder, since that is the folder you ran wget from.

If you have trouble finding something, the "locate" command is useful. First, update the database:

```
sudo updatedb
```Then run locate, in this case you're looking for "calligra-latest"

```
locate calligra-latest
```It should find you the right folder location instantly.

You could also install [recoll]("http://www.lesbonscomptes.com/recoll/features.html"), which is a good file indexer and is simple to use.  It not only lets you search for filenames, but also the text within files.

I think KDE has something like that running as standard, not sure if Gnome does, but I see recoll has now got a [Unity lens]("http://www.webupd8.org/2012/03/recoll-lens-full-text-search-unity-lens.html").

.

Thanks for that :popcorn:. I now know the search thingummy I do have is not as good as I thoght. I will have a look at some of those others. For no apparent reasonthe 2.6 calligra download was under 'templates.'

I have managed to extract the files. So far so good and now it is on my desktop.

Now all I need to understand is how to get the whole thing to work! I can open and read the individual files in calligra- some of them, but am not sure how to actually execute  the whole thing...just lost on where .exe is?

---

### Post by Jackalyn on 2012-09-21
> **Jackalyn said:**
> Thanks for that :popcorn:. I now know the search thingummy I do have is not as good as I thoght. I will have a look at some of those others. For no apparent reasonthe 2.6 calligra download was under 'templates.'

I have managed to extract the files. So far so good and now it is on my desktop.

Now all I need to understand is how to get the whole thing to work! I can open and read the individual files in calligra- some of them, but am not sure how to actually execute  the whole thing...just lost on where .exe is?

Wow and thanks...recoll will be so useful to someone like me who often remembers text and can't think where they wrote something.

---

### Post by Jackalyn on 2012-09-21
I think the problem is that the instructions to say run *intrepo.sh*  i  just cannot seem to do that? Calligra itself does not recognise it? (Made it executable.)

---

### Post by Jackalyn on 2012-10-10
Just to say I finally resolved how to get the components of Calligra Author which is in Beta into Calligra 2.5.  It occurred to me that as I had all the files for Author I could merge them with Calligra 2.5 and this got me where I needed to be. I think.  OOOPS No I didn't! However have a lot more functionality in Calligra than before?

I am not yet impressed with Calligra over other things writers of books can use though but seeing it is in the making, I can do what I wanted to see it for and send them feedback.

To be honest, what is needed is a publisher who is also a programmer who writes their own books/

---


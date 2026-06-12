---
title: "make error with gtkpod SVN. For the love of god help me."
date: 2008-07-20
forum: Packaging and Compiling Programs
---

### Post by nimbis on 2008-07-20
I started using Ubuntu Gutsy about 6 months or so ago, and the only thing that keeps it from being perfect is that I can't transfer .mp4 movies to my iPod with gtkpod. 
Whenever I tried to transfer mp4s with the version of gtkpod in the Gutsy repos, I got this message:

[INDENT][/INDENT]```
"Import of 'movie.mp4' failed: m4a/m4p/m4b not supported without the mp4v2 library. You must compile the gtkpod source together with the mp4v2 library. 
The following track could not be processed (filetype is known but analysis failed): 'movie.mp4'
```

A few months ago, this statement terrified me, but since then I've become comfortable with compiling and all that, and I thought I'd give it a go.
I grabbed a libmp4v2 tarball from [http://resare.com/libmp4v2/dist/]("http://resare.com/libmp4v2/dist/"). I successfully compiled it, and installed it with checkinstall.

I then got the latest SVN of gtkpod from this command:
```
 svn co https://gtkpod.svn.sourceforge.net/svnroot/gtkpod gtkpod 

```

First I compiled the libgpod trunk directory that I got from that command, and I installed it (without checkinstall, it didn't work that way for some reason)
Then I went into the gtkpod trunk directory, and attemped to build it with these commands:
```
./autogen.sh

```
This command revealed this line near the end:
```
 mp4v2 ................: yes -- will build with aac support

```
That's good, I thought, that means that I installed libmp4v2 correctly! :)
I then attempted to make it:
```
make
```
and got this output at the end of the process:
```
display_playlists.o: In function `pm_selection_changed_cb':
/home/freman/gtkpod/gtkpod/trunk/src/display_playlists.c:1535: undefined reference to `g_warn_if_reached'
collect2: ld returned 1 exit status
make[2]: *** [gtkpod] Error 1
make[2]: Leaving directory `/home/freman/gtkpod/gtkpod/trunk/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/freman/gtkpod/gtkpod/trunk'
make: *** [all] Error 2

```
I am so, so close. I can taste it. How do I get over this last hurdle?

---

### Post by nimbis on 2008-07-24
Bump.

I've seen posts on threads of people having successfully compiled gtkpod with libmp4v2. I've got every neccessary compiling library and tool that I can think of, and it still won't work.

If anybody has successfully compiled it, could you please point me to the specific version that worked for you?

---

### Post by nimbis on 2008-07-31
Thanks for all the help guys....

Anyway, for those that are interested, if you just want to put .mp4 files onto your iPod, I found this way that sidesteps the necessity of compiling gtkpod with libmp4v2.

1) Rename your .mp4 files to .mov:```
for i in *.mp4 ; do mv "$i" "${i%mp4*}mov" ; done

``` 
2) Now go into gtkpod, and click-and-drag them in or add them through the menus.
3) Now right click on the movie when it's inside gtkpod and select "Edit track details"
4) Type in the length of the movie in both "Play time" and "Stop time".
5) Update your iPod. The movies should now be working.

This worked for me on Ubuntu Gutsy 7.10, with a 2 week old iPod Classic 80GB. Hope this helped somebody.

---


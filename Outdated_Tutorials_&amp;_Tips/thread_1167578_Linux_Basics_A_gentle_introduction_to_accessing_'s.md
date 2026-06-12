---
title: "Linux Basics: A gentle introduction to accessing 'svn' repositories"
date: 2009-05-23
forum: Outdated Tutorials &amp; Tips
---

### Post by andrew.46 on 2009-05-23
===================
**Introduction**
===================

This is the second of a projected series of guides aimed at giving beginning users of Ubuntu a gentle introduction into some of the more fundamental tools available in Linux. This particular guide deals with 'svn', a great commandline tool for controlling, manipulating and accessing software held in subversion repositories. I will not however be dealing with setting up an svn repository or committing changes to such a repository in this introductory guide but simply with accessing such a repository as an end-user. Perhaps a future guide will deal with the other side of svn...

Can I emphasis right at the beginning: *Using 'svn' is easy!!*. This guide, similar to other guides in this series, will walk through a real-world example and will be best followed by duplicating the steps I am demonstrating on your own computer and perhaps experimenting a little on the way. And remember "Have Fun!!".

================================
**The basic use of 'svn'**
================================

FFmpeg usage is very active on the Ubuntu Forums so our 'real-world' example will deal with the FFmpeg subversion repository although it could as easily be the MPlayer or vlc repositories. First we move to the Desktop and download the FFmpeg subversion subdirectory we require and place it in a directory called 'ffmpeg':

```

$ cd $HOME/Desktop
$ **[COLOR="Purple"]svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg[/COLOR]**

```

There you have the source code for the latest svn FFmpeg neatly filed away on your Desktop. Can you see how easy the usage of 'svn' is? This source code contains a large amount of 'versioning' infomation to allow you to upgrade and downgrade your downloaded source code which accounts for the slightly bloated 38 megabyte size of this directory. If you wanted to get a copy without this information you would use 'export' rather than 'checkout' but bear in mind that this cannot subsequently be updated. So what version of FFmpeg have we downloaded? Use the following command to see the local version information:

```

$ cd $HOME/Desktop/ffmpeg
$ **[COLOR="Purple"]svn info[/COLOR]**
Path: .
URL: svn://svn.ffmpeg.org/ffmpeg/trunk
Repository Root: svn://svn.ffmpeg.org/ffmpeg
Repository UUID: 9553f0bf-9b14-0410-a0b8-cfaf0461ba5b
Revision: 18905
Node Kind: directory
Schedule: normal
Last Changed Author: bcoudurier
Last Changed Rev: 18905
Last Changed Date: 2009-05-23 11:22:43 +1000 (Sat, 23 May 2009)

```

And there we can see the revision number, the date and author of the change but we cannot see the nature of this change. For this the following command is required:

```

$ cd $HOME/Desktop/ffmpeg
$ **[COLOR="Purple"]svn log -r 18905[/COLOR]**
------------------------------------------------------------------------
r18905 | bcoudurier | 2009-05-23 11:22:43 +1000 (Sat, 23 May 2009) | 3 lines

Set progressive_sequence before MPV_common_init which cares about it when
setting mb_height for interlaced mpeg-2 encoding.

------------------------------------------------------------------------

```

There are all the details of the changes made by revision r18905, understanding of these actual changes I leave to you :-). If you are a little curious about the last four changes to the FFmpeg subversion repository you can issue the following command:

```

$ cd $HOME/Desktop/ffmpeg
$ **[COLOR="Purple"]svn log --limit 4[/COLOR]**

```

and the last 4 revision logs will be nicely formatted and presented on your terminal. You can of course substitute any number here but be aware this command can sometimes take a little while to run. The final command that is useful at a basic level of svn usage is probably the most important one, 'svn update' or its shortened form 'svn up':

```

$ cd $HOME/Desktop/ffmpeg
$ **[COLOR="Purple"]svn up[/COLOR]**
U    libavformat/gxfenc.c
U    libavformat/mxfenc.c

Fetching external item into 'libswscale'
Updated external to revision 29318.

Updated to revision 18906.

```

You can see that now our copy has been updated to revision 18906 and we are given the details of the various files that have been updated. Can you remember me saying before: *Using 'svn' is easy!!*

=================================
**Moving beyond the basics**
=================================

To tell the truth the information given above will be sufficient for 90% of usage of svn but of course there will be times when things go wrong and then we need to dig out a few more commands from our svn arsenal. Perhaps revision 18906 is more than a little disastrous and we need to return to the successful version r18905, the following command will do exactly this:

```

$ cd $HOME/Desktop/ffmpeg
$ **[COLOR="Purple"]svn up --revision 18905[/COLOR]**
U    libavformat/gxfenc.c
U    libavformat/mxfenc.c

Fetching external item into 'libswscale'
Updated external to revision 29318.

Updated to revision 18905.

```

The shortened form of '--revision', which is simply '-r', can be used if you prefer. So now we have returned safely to our previous working version. But what if there is a power surge, a network outage or a computer malfunction while you are interacting with the subversion repository? This can often leave your local version of the repository locked with an error message such as: 'svn: Working copy 'ffmpeg' locked'. The following command should fix this condition by recursively cleaning up the working copy, removing locks, resuming unfinished operations, etc:

```

$ cd $HOME/Desktop/ffmpeg
$ **[COLOR="Purple"]svn cleanup .[/COLOR]**

```

And you should now be able to use the FFmpeg source again. In a final note to this section I have to unfortunately dispel the illusion that I know such an *amazing* amount about the svn command line! All of the information that I have mentioned so far is easily seen by accessing svn 'help'. A list of help *topics* can be seen by issuing the following command:

```

$ **[COLOR="Purple"]svn help[/COLOR]**

```

So to see details of the 'cleanup' command I have just illustrated you would run:

```

$ **[COLOR="Purple"]svn help cleanup[/COLOR]**
cleanup: Recursively clean up the working copy, removing locks, resuming
unfinished operations, etc.
usage: cleanup [PATH...]

Valid options:
  --diff3-cmd ARG          : use ARG as merge command

Global options:
  --username ARG           : specify a username ARG
  --password ARG           : specify a password ARG
  --no-auth-cache          : do not cache authentication tokens
  --non-interactive        : do no interactive prompting
  --config-dir ARG         : read user configuration files from directory ARG

```
 
The same syntax will reveal the intimate details of all of the other commands I have mentioned such as 'checkout', 'update' and 'log' as well as revealing many others that I have not even touched upon.

=================================
**Advanced usage of 'svn'**
=================================

I believe that the preceding sections have comprehensively covered the needs of about 99% of casual svn users but for those who perhaps want a little more there is this final section. Are you a little curious to see the exact code changes between revision 18905 and revision 18906? If so then you can use 'svn diff' as follows:

```

$ cd $HOME/Desktop/ffmpeg
$ **[COLOR="Purple"]svn diff -r 18905:18906[/COLOR]**
Index: libavformat/gxfenc.c
===================================================================
--- libavformat/gxfenc.c	(revision 18905)
+++ libavformat/gxfenc.c	(revision 18906)
@@ -19,7 +19,6 @@
  * Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA
  */
 
-#include "libavutil/fifo.h"
 #include "avformat.h"
 #include "gxf.h"
 #include "riff.h"
Index: libavformat/mxfenc.c
===================================================================
--- libavformat/mxfenc.c	(revision 18905)
+++ libavformat/mxfenc.c	(revision 18906)
@@ -35,7 +35,6 @@
 #include <math.h>
 #include <time.h>
 
-#include "libavutil/fifo.h"
 #include "libavutil/random_seed.h"

 #include "libavcodec/bytestream.h"


 #include "audiointerleave.h"

```

And there are the changes conveniently laid out as a patch. 'svn diff' has many, many options that can of course be examined closely with 'svn help diff'. One of the most interesting for advanced users is the ability to write your own patches against the svn tree. First run 'svn up' and then make a small change in the FFmpeg source code; for the purpose of this demonstration I have altered one of the ffpreset files. Now run the following:

```

$ cd $HOME/Desktop/ffmpeg
$ **[COLOR="Purple"]svn diff > ../ffpreset.diff[/COLOR]**

```

Now open the file $HOME/Desktop/ffpreset.diff and you will see:

```

Index: ffpresets/libx264-lossless_ultrafast.ffpreset
===================================================================
--- ffpresets/libx264-lossless_ultrafast.ffpreset	(revision 18907)
+++ ffpresets/libx264-lossless_ultrafast.ffpreset	(working copy)
@@ -6,6 +6,7 @@
 subq=0
 me_range=16
 g=250
+This is a demonstration of 'svn diff'
 keyint_min=25
 sc_threshold=40
 i_qfactor=0.71


```

And there in living glory is your first patch on the subversion FFmpeg! You could submit this to the FFmpeg developers but you might be better to use yet another svn command to quietly lose this change:

```

$ cd $HOME/Desktop/ffmpeg
$ **[COLOR="Purple"]svn revert . -R[/COLOR]**
Reverted 'ffpresets/libx264-lossless_ultrafast.ffpreset'

```

That is about all I have to offer on this introductory guide to the use of svn. If you wish to read a little further an excellent starting point would be [Version Control with Subversion]("http://svnbook.red-bean.com/"), a site that I used extensively in the writing of this guide.

=================================
**And in conclusion...**
=================================

Old hands in the Linux world know that this brief guide illustrates just the bare beginnings of 'svn' usage. In particular it does not deal with the heart and soul of subversion where repositories are created and changes are committed, reverted, commented upon etc by multiple developers. But if this guide has managed to give anybody even the barest and most practical beginning to svn usage my goal has been achieved!

May 23rd, 2009.
Andrew Strong

---

### Post by wieman01 on 2009-05-23
Nice one, Andrew. This will come in handy one day.

---

### Post by andrew.46 on 2009-05-23
Hi wieman01,

> **wieman01 said:**
> Nice one, Andrew. This will come in handy one day.

Thanks both for your kind words for getting this guide into the 'Tutorials and Tips' section within 60 minutes of me posting it :-).

Andrew

---

### Post by wieman01 on 2009-05-23
> **andrew.46 said:**
> Hi wieman01,

Thanks both for your kind words for getting this guide into the 'Tutorials and Tips' section within 60 minutes of me posting it :-).

Andrew
Not a problem, but the short lead-time is pure coincidence. :-)

---

### Post by DanCas on 2009-08-18
Thanks, helpful

---

### Post by andrew.46 on 2009-08-19
Hi DanCas,

> **DanCas said:**
> Thanks, helpful

My pleasure :-). Actually I am tickled pink that someone has not only found this guide but found it useful as well!

Andrew

---

### Post by kevdog on 2009-08-19
Although a little bit off topic, is there a way with the different revision numbers and such to generate a patch file, and then later apply the patch.  Is diff the utility to create patch files?

---

### Post by ra3don on 2009-08-19
Awesome guide, thanks for this. I was always wondering how to use SVN and this has answered the question for me, i never knew it was so powerful. Thanks once again for the great tutorial!

---

### Post by wieman01 on 2009-08-19
> **andrew.46 said:**
> Hi DanCas,



My pleasure :-). Actually I am tickled pink that someone has not only found this guide but found it useful as well!

Andrew
That... happens. :-)

---

### Post by andrew.46 on 2009-08-19
Hi ra3don,

> **ra3don said:**
> I was always wondering how to use SVN and this has answered the question for me, i never knew it was so powerful.

Well of course this little guide actually only deals with a small part of the use of svn. The rest of the power of svn comes with setting up your own svn repository or utilising *write* permission to a remote repository. But for most of us the ability to download from an svn repository and use some of the techniques I have described is more than enough ;-).

All the best,

Andrew

---

### Post by andrew.46 on 2009-08-19
Hi kevdog,

> **kevdog said:**
> Although a little bit off topic, is there a way with the different revision numbers and such to generate a patch file, and then later apply the patch.  Is diff the utility to create patch files?

In any guide I have ever written there is no 'off topic', I always enjoy moving beyond a set topic :-).To produce an actual patch is a simple variation of one of the methods I described in the 'Advanced' section, the difference simply being use of '>' to redirect the output to a file. So to produce a patch that demonstrates the difference between revision 18905 and revision 18906:

```

svn diff svn://svn.ffmpeg.org/ffmpeg/trunk -r 18905:18906 > $HOME/Desktop/changes.diff

```

will produce a nice formatted diff and you do not even need any of the standard diff options.

All the best,

Andrew

---

### Post by kevdog on 2009-08-20
So I'm taking, you could apply this patch to the older svn repository to update it?  Yea I know this seems silly, but I've run into some examples when I might want to use this utility.

---

### Post by andrew.46 on 2009-08-20
Hi kevdog,

> **kevdog said:**
> So I'm taking, you could apply this patch to the older svn repository to update it?  Yea I know this seems silly, but I've run into some examples when I might want to use this utility.

You would be a little lucky to have a patch like this apply *cleanly* to older versions but at the very least you could examine the change and attempt to replicate it with similar changes to the older source code. I have done this myself and it is a lot of fun as long as you are prepared for some unpredictable results :-).

The only effort of my own produced in this way that I would every acknowledge was a patch to allow a custom OS to be used in the User-Agent string for slrn:

[http://andrews-corner.org/custom_os.patch](http://andrews-corner.org/custom_os.patch)

But I produced this in the same manner that you have mentioned, with a bit of extra work and advice from others mind you...

Andrew

---

### Post by jumboa7 on 2009-08-21
I like the short and get-to-the-point style of your article. It would be great if there will be article related in how to use svn to help patching ubuntu project.

Thanks,

---

### Post by kevdog on 2009-08-22
Thanks for the advice and real world experience.  I could really use a primer on the use and production of patch files.

---


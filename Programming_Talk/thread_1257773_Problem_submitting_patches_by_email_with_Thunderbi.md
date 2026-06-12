---
title: "Problem submitting patches by email with Thunderbird"
date: 2009-09-04
forum: Programming Talk
---

### Post by WebDrake on 2009-09-04
Hello all,

I've recently started contributing documentation to Lilypond:
[http://www.lilypond.org/](http://www.lilypond.org/)

They use git as their revision control system, so the process of submitting patches goes roughly like this:
[LIST=1]
[*]I edit the code and commit to my local branch
[*]I use 'git format-patch origin' to generate a patch
[*]I email the files to the lilypond-devel mailing list for review
[/LIST]
The problem is, the docs maintainer is receiving the patches with DOS line-endings.  I'm editing the code/texinfo files in Kate (on Kubuntu 9.10) with utf-8 encoding and UNIX line endings selected, so I don't think the problem is with the actual patches I'm generating.  Rather, I think they're being mangled when sent as email attachments with Thunderbird.

The docs maintainer uses Windows but does not believe this to be a problem as he receives patches without problem from other contributors.

So, questions.

First, how can I check if my patch files really are using UNIX line endings?  Just to be certain.

Second, assuming Thunderbird to be the problem, how can I set it up to not mangle my patches?  Currently the config option mail.content_disposition_type is set to 1 (meaning all attachments are sent as *attachments* and not inline), and emails are sent as plain text encoded in utf-8.

For reference, I'm attaching the source of the most recent patch email I submitted (I've blanked out my email address, but all the rest is as was).  The docs maintainer has pointed to the Content-Transfer-Encoding: 7bit as being the possibly responsible part, but I have no idea how to change this.

If not this, any other ideas for why the patches should be winding up with DOS line-endings?

Thanks & best wishes,

    -- Joe

```

This is a multi-part message in MIME format.
--------------000005020808060804080604
Content-Type: text/plain; charset=UTF-8
Content-Transfer-Encoding: 7bit

Hello everyone,

As discussed on the -user list, this is a patch to start a section in
the Specialist Notation chapter on contemporary music.

Currently it's just a menu of general sub-headings -- more will follow
in the next days.  It's intended to provide both a unified collection of
references to the existing documentation on contemporary notational
techniques along with extensive examples, snippets and so on.

I really hope that this patch (or rather, this email containing the
patch:-) has avoided the DOS line endings.  I've tested it on a fresh
git branch by emailing it to myself with new Thunderbird settings and it
applies cleanly.

If not, further work on this section may be slightly delayed as I seek
out Thunderbird developers to beat over the head until they offer a
solution ...

Best wishes,

    -- Joe

--------------000005020808060804080604
Content-Type: text/x-diff;
 name="0001-Contemporary-music-overview-of-new-specialist-notati.patch"
Content-Transfer-Encoding: 7bit
Content-Disposition: attachment;
 filename*0="0001-Contemporary-music-overview-of-new-specialist-notati.pa";
 filename*1="tch"

>From 21d8e5c7c6ab79f8fde0872ec16455fc183ac233 Mon Sep 17 00:00:00 2001
From: Joseph Wakeling <------.--------@--------.--->
Date: Fri, 4 Sep 2009 01:27:10 +0200
Subject: [PATCH] Contemporary music: overview of new specialist notation section.

---
 Documentation/notation/contemporary.itely |   51 +++++++++++++++++++++++++++++
 Documentation/notation/specialist.itely   |    2 +
 2 files changed, 53 insertions(+), 0 deletions(-)
 create mode 100644 Documentation/notation/contemporary.itely

diff --git a/Documentation/notation/contemporary.itely b/Documentation/notation/contemporary.itely
new file mode 100644
index 0000000..cd424b8
--- /dev/null
+++ b/Documentation/notation/contemporary.itely
@@ -0,0 +1,51 @@
+@c -*- coding: utf-8; mode: texinfo; -*-
+@ignore
+    Translation of GIT committish: FILL-IN-HEAD-COMMITTISH
+
+    When revising a translation, copy the HEAD committish of the
+    version that you are working on.  See TRANSLATION for details.
+@end ignore
+
+@c \version "2.13.4"
+
+
+@node Contemporary music
+@section Contemporary music
+
+From the beginning of the 20th Century there has been a massive
+expansion of compositional style and technique.  New harmonic
+and rhythmic developments, an expansion of the pitch spectrum
+and the development of a wide range of new instrumental
+techniques have been accompanied by a parallel evolution and
+expansion of musical notation.  The purpose of this section is
+to provide references and information relevant to working with
+these new notational techniques.
+
+@menu
+* Pitches and harmony in contemporary music::
+* Contemporary approaches to rhythm::
+* Graphical notation::
+* Contemporary scoring techniques::
+* New instrumental techniques::
+@end menu
+
+
+@node Pitches and harmony in contemporary music
+@subsection Pitches and harmony in contemporary music
+
+
+@node Contemporary approaches to rhythm
+@subsection Contemporary approaches to rhythm
+
+
+@node Graphical notation
+@subsection Graphical notation
+
+
+@node Contemporary scoring techniques
+@subsection Contemporary scoring techniques
+
+
+@node New instrumental techniques
+@subsection New instrumental techniques
+
diff --git a/Documentation/notation/specialist.itely b/Documentation/notation/specialist.itely
index e98730c..8aafd12 100644
--- a/Documentation/notation/specialist.itely
+++ b/Documentation/notation/specialist.itely
@@ -24,6 +24,7 @@ types of instrument or in specific styles.
 * Chord notation::
 * Ancient notation::
 * World music::
+* Contemporary music::
 @end menu
 
 @include notation/vocal.itely
@@ -35,4 +36,5 @@ types of instrument or in specific styles.
 @include notation/chords.itely
 @include notation/ancient.itely
 @include notation/world.itely
+@include notation/contemporary.itely
 
-- 
1.6.3.3


--------------000005020808060804080604
Content-Type: text/plain; charset="us-ascii"
MIME-Version: 1.0
Content-Transfer-Encoding: 7bit
Content-Disposition: inline

_______________________________________________
lilypond-devel mailing list
lilypond-devel@gnu.org
http://lists.gnu.org/mailman/listinfo/lilypond-devel

--------------000005020808060804080604--
```

---

### Post by tturrisi on 2009-09-04
zip 'em.

---

### Post by WebDrake on 2009-09-06
> **tturrisi said:**
> zip 'em.

OK, this is one way. :-)

I was kind of hoping there was an alternative -- a way of changing the Content-Type-Encoding for the attachments.  I tried using git send-email but that either just sends the patch inline (not what the maintainer wants, and it winds up having DOS line-endings just the same) or, if I use the git format-patch --attach option, it generates an attached patch but missing the patch description.

Ah well.  Zip it is then. :-(

---

### Post by WebDrake on 2009-10-19
The solution is actually surprisingly simple.  Thunderbird applies a different mime-type to files whose name ends in .patch.  It turned out that all that was necessary was for the filename to end in .txt ... :-P

---


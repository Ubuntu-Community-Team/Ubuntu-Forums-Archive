---
title: "[SOLVED] Editing gedit html.tags -- a question"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by L a r r y on 2008-06-09
Hi all,

I am editing the HTML tags available in the side panel of gedit, by editing the html.tags XML file.  I obtained the [_idea from this source_]("http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html").  I downloaded his alphabetical listing and am reorganizing it into tags relative to the head and then the body.

The source web site states:
> To update the contents of the tagslist, you will first need to download my tag files (gedit_webdev_tags-0.1.tar.gz) and copy them to wherever your gedit tags are stored. 
On ubuntu, it's in /usr/share/gedit-2/taglist/

Here on my Ubuntu 8.04 LTX, all I find under /usr/share/gedit-2/taglist/ is html.tags.gz, and a search does not uncover any other uncompressed tags file.

Does this mean gedit reads its settings from the compressed gz file?
_**YES.**_

Secondly, when I finish my edit, I will replace the existing file, after I back it up.  How do I go about compressing the file to create the gz?
[U][B]ON THE WORKING COPY ON THE DESKTOP, RIGHT-CLICK AND SELECT "Create Archive..." AND MAKE A .gz.

NEXT, DO A gksudo cp COMMAND TO COPY THE .gz INTO GEDIT'S taglist FOLDER. [/B][/U]

It would be neat if I could also add keyboard macros, so that I could hit ctrl-space to enter a nonbreaking space.  I use that at the ends of sentences to acquire the double-space between sentences.  Is there any chance of this?
_**APPARENTLY NOT, AS FAR AS I HAVR DETERMINED.**_
Thank you for any help!

Larry

---

### Post by L a r r y on 2008-06-13
This was a Bump message that I shortened with intent of deleting it...

---

### Post by L a r r y on 2008-06-15
This thread is solved.

---


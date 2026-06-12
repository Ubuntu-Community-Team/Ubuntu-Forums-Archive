---
title: "Emacs Drag n Drop AND Nautilus Open in Emacs Script"
date: 2007-01-04
forum: Programming Talk
---

### Post by lukew on 2007-01-04
Hi,

I seem to be getting nowhere trying to find answers for the following two questions about opening files in emacs.  Any help is much apreciated.

1. I can not drag and drop text / files into emacs. I can do this for other applications. GUN Help pages states that it is possible.

2. My Nautilus Script - Open in Emacs does not work when there are spaces in the file name. This script works for other applications when there are spaces in the file name. Any ideas? The is opened with %20 instead of spaces but no contents!!

```
#!/bin/bash
#
# Opes the file in Emacs.

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	emacs21 "$uri"	
done

```

Any help is much apreciated.

Thanks

Luke

---

### Post by duff on 2007-01-04
I don't know about a bash way to unescape a URI, but you could always use python for your launching script.  **urllib.url2pathname** for unescaping the path, and **os.system** for starting emacs.

```
>>> import urllib
>>> urllib.url2pathname('file:///home/bob/foo%20bar')[7:]
'/home/bob/foo bar'
```

---

### Post by lukew on 2007-01-06
Hay DUFF!!

Thanks for the reply.

This is strange because it works for all the other scripts where i send a file to an application, just emacs fails!!

Still can not figure out why files can not be dragged onto emacs to open up!! 

Never done any python before so might perservere a bit longer.

Thanks once more for the help.

Luke

---

### Post by lukew on 2007-01-09
> **lukew said:**
> Hay DUFF!!

Thanks for the reply.

This is strange because it works for all the other scripts where i send a file to an application, just emacs fails!!

Still can not figure out why files can not be dragged onto emacs to open up!! 

Never done any python before so might perservere a bit longer.

Thanks once more for the help.

Luke

Hi,

Not to wory. I have started using emacsclient, the "problem" seems to have been solved.

Cheers

Luke

---

### Post by kwhitefoot on 2007-05-19
I tried adding emacsclient to the Open With menu in Nautilus but nothing happens.  
There is no need to put problem in quotation marks it really is a problem.  Opening a file in another instance of Emacs prevents proper use of Emacs.

If I try running emacsclient from the command line I get an error message:

emacsclient: can't stat /tmp/esrv1000-vimes: Success

(vimes is the host name).

---

### Post by lukew on 2007-06-01
> **kwhitefoot said:**
> I tried adding emacsclient to the Open With menu in Nautilus but nothing happens.  
There is no need to put problem in quotation marks it really is a problem.  Opening a file in another instance of Emacs prevents proper use of Emacs.

If I try running emacsclient from the command line I get an error message:

emacsclient: can't stat /tmp/esrv1000-vimes: Success

(vimes is the host name).

Place the following in you .emacs

```
(server-start)
```

Open emacs normally.

Once emacs is open you can then open a file with emacsclient or emacsclient.emacs-snapshot depending upon which version you are using.

Luke

---


---
title: "mutt and mailcap"
date: 2005-12-31
forum: Programming Talk
---

### Post by rosslaird on 2005-12-31
This may not be the correct forum, so apologies in advance if so, but no other forum seemed quite right. So here goes:

I'm having trouble getting mutt to open MS Word files (attachments with .doc extension). Mutt says there is no matching mailcap entry. In my .mailcap file (in ~/), I have this:

```

application/msword;             /usr/bin/abiword '%s'; test=test "$DISPLAY" != ""; \
description=Microsoft Word; nameplate=%s.doc
application/msword;             word2text %s; copiousoutput
application/vnd.msword;         mutt_bgrun openoffice %s; test=RunningX
application/vnd.msword;         word2text %s; copiousoutput
#
```

As you can see, I've tried various things. Any help would be appreciated. I'm finding the mailcap file to be quite cryptic.

Ross


EDIT:

OK, got it. It wasn't mutt's fault. I found this:

Fixing broken Content-Type:

> A common problem, particularly with mailers from the windows world that rely on file-extensions for identifying content-types, is that many attachments are mis-labelled as the generic Content-Type: octet/stream.

You can temporarily fix the content-type of a mime part using the edit-type command, bound to Ctrl-e in the attach menu. This can get tedious if you receive lots of octet/stream attachments - If so, then you may want to install mutt octet filter, a tool that tries to identify the real content-type of attachments.


It's on this very useful site: [http://www.mutt.blackfish.org.uk/attachments/](http://www.mutt.blackfish.org.uk/attachments/)

It's working now.

---


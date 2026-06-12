---
title: "cgi upload problem"
date: 2006-10-19
forum: Programming Talk
---

### Post by pjkoczan on 2006-10-19
I have a bit of a programming snafu when uploading files. I have two separate but related problems when it comes to said uploads.

1. When doing a sanity check (i.e. "This file is about to be overwritten, continue?"), I lose the filehandle and the file is deleted once the CGI script is done exec'ing.

2. If a user suddenly gets unauthenticated when trying to upload (corrupt cookies, perhaps), they again lose the filehandle and file. I could always say that the upload failed and to try again, but it'd be nice to have it just work.

I could, in theory, save the file to a temporary location and pass the filename to deal with it later, but that opens things up to hacking, potential wasted disk space, and, worst of all, race conditions. Does anyone have any techniques for dealing with this? In other words, is there any nice way to pass a file upload beyond that first page?

One of the problems is that Firefox, for instance, only uses the basename of the file when you get the filename.

I'm using perl and the associated CGI modules. Thanks much.

PDK

P.S. Sorry for being verbose, it's just my way when describing problems.

---


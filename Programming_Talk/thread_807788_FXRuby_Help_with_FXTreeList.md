---
title: "FXRuby Help with FXTreeList"
date: 2008-05-26
forum: Programming Talk
---

### Post by mordantae on 2008-05-26
Hi,
i'm pretty new to both ruby and fxruby, and im currently trying to work
my way through writing my first program but i've run into a bit of a
ditch trying to work out what i need. Let me elaborate.

I'm trying to make a program that will allow the user to create and
manage a 'visual' database of (for example) a cd collection. I want the
information inside the database to be in the form of a heirarchical list
like FXTreeList and FXDirList objects are, however i'm stumped in
relation to FXTreeList and FXDirList in the following ways:

How can i fill FXTreeList (or a more appropriate class of object) with
the relevant data? I want to be able to navigate to a directory and have
an instance of the tree list be created with only the relevant directory
structure inside. I've made DirLists which give me access to my entire
filesystem but i can't figure out where to pass the location of the
starting directory to.

I'm thinking perhaps a dirlist is simply an instance of that nature(tree
list like navigation through entire filesystem), hence my looking into
the treelist object..

How can i 'save' a TreeList? I followed a really good book "Create Lean
Mean Guis with Ruby" and the tutorial makes use of YAML to store the
state of the program (photos added to albums) for the next time the
program starts? Firstly would i be able to use yaml to store these 'tree
lists'...?

and secondly what about offering the user the option to 'save' to a
location on disk so that if something dictated the program had to be
reinstalled they wouldn't lose all their database data they so
painstakingly added...?

I've been trawling the internet and re-reading the FXrRuby Rdoc online
but i can't seem to get my head round this particular information..

Any help whatsoever would be greatly appreciated, even if you want to
just redirect me to somewhere i can read about this further would be
fine...

Thought i'd try posting this question here as well as on ruby-forum.com since this forum is one of the most helpful i've had ever since i started using linux 5 months ago...i've gone from total beginner "what are all these commands? never typed inside a terminal" to now studying for an LPIC (soon finishing course for LP101, LP102 will follow) and my love for linux is growgrowgrowing. (even installed ubuntu on my mum's ( a **very** basic computer user) laptop and am teaching and looking after her and fixing her problems hehehe).


Best regards
T.Kingswell

---


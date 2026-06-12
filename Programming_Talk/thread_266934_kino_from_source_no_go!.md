---
title: "kino from source no go!"
date: 2006-09-27
forum: Programming Talk
---

### Post by koshari on 2006-09-27
iam trying to install kino latest stable version from source as the one in the repo is broken (ieee1394 transfers in type2 fail)

unfortinately when i run confure it doesnt see libdv
> checking for LIBDV... configure: error: Package requirements (libdv >= 0.103) were not met:

No package 'libdv' found

however synaptic says its installed

thers is another post on the kino forum that has the same issue;
[http://www.kinodv.org/dcforum/dcforum?az=show_topic&forum=101&topic_id=2361&mesg_id=2372](http://www.kinodv.org/dcforum/dcforum?az=show_topic&forum=101&topic_id=2361&mesg_id=2372)

and gives some advice to "Consider adjusting the PKG_CONFIG_PATH environment variable if you installed software in a non-standard prefix." but its out of my league.

any help woud be appreaciated.

---

### Post by koshari on 2006-09-28
looks like i needed the dev versions installed, 

[http://www.ubuntuforums.org/archive/index.php/t-203022.html](http://www.ubuntuforums.org/archive/index.php/t-203022.html)

over this little hurdle now :-)

---


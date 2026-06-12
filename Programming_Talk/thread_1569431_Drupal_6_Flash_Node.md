---
title: "Drupal 6: Flash Node"
date: 2010-09-06
forum: Programming Talk
---

### Post by steve_c on 2010-09-06
Has anyone tried using Drupal 6 as installed by Ubuntu 10.04 with Flash Node to create/manage Flash video content?

I'm running into a problem where the videos aren't displaying--it's linking to a file that doesn't exist:
```
<param name="movie" value="http://localhost/drupal6/sites/default/files//var/lib/drupal6/files/flash/ascent.swf" /> 
```

Near as I can tell the problem seems to be that Flash Node is combining both the URL where it *should* be pointing (localhost/drupal6/sites/default/files/) with the *real* system path to the flash file. My suspicion is that this has something to do with Ubuntu's use of symlinking the /etc/drupal/6/sites/default/files to /var/lib/drupal6/files.

I've been poking around the Flash Node module code for hours now and can't seem to figure out how to change this one little thing and make the stupid videos work, so I'm coming here as a last appeal for help before I cave and try to use a different solution.

Thanks for any advice.

---


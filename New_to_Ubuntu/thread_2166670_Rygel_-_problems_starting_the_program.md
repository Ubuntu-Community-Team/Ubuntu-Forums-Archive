---
title: "Rygel - problems starting the program"
date: 2013-08-10
forum: New to Ubuntu
---

### Post by Krabun on 2013-08-10
Ubuntu 13.03
Rygel 0.18.0-1 (optional addons onstalled)
Execute permission in rygel and rygel.conf

Does anybody know how to start Rygel. Logged in as root through sudo su. I'm trying to do it from the terminal using 'Rygel' and then I get this:

(rygel:6329): Rygel-CRITICAL **: string_replace: assertion `replacement 0.18.0-10.18.0-1!= NULL' failed
Rygel-Tracker-Message: rygel-tracker-item-factory.vala:66: Using none as upload directory for object.item.audioItem.musicTrack

(rygel:6329): GLib-CRITICAL **: g_filename_to_uri: assertion `filename != NULL' failed

(rygel:6329): Rygel-CRITICAL **: string_replace: assertion `replacement 0.18.0-1!= NULL' failed
Rygel-Tracker-Message: rygel-tracker-item-factory.vala:66: Using none as0.18.0-1 upload directory for object.item.videoItem

(rygel:6329): GLib-CRITICAL **: g_filename_to_uri: assertion `filename != NULL' failed

(rygel:6329): Rygel-CRITICAL **: string_replace: assertion `replacement != NULL' failed
Rygel-Tracker-Message: rygel-tracker-item-factory.vala:66: Using none as upload directory for object.item.imageItem.photo
0.18.0-1
(rygel:6329): GLib-CRITICAL **: g_filename_to_uri: assertion `filename != NULL' failed
Rygel-Message: New plugin 'Tracker' available
Rygel-Message: New plugin 'Playbin' available
Mediathek-Message: rygel-mediathek-plugin.vala:33: Plugin 'ZDFMediathek' disabled by user, ignoring..
MPRIS-Message: rygel-mpris-plugin-factory.vala:33: Module 'MPRIS' disabled by user. Ign(rygel:6329): Rygel-CRITICAL **: string_replace: assertion `replacement != NULL' failed
Rygel-Tracker-Message: rygel-tracker-item-factory.vala:66: Using none as upload directory for object.item.audioItem.musicTrack
0.18.0-10.18.0-1
(rygel:6329): GLib-CRITICAL **: g_filename_to_uri: assertion `filename != NULL' failed

(rygel:6329): Rygel-CRITICAL **: string_replace: assertion `replacement != NULL' failed
Rygel-Tracker-Message: rygel-tracker-item-factory.vala:66: Using none as upload directory for object.item.videoItem

(rygel:6329): GLib-CRITICAL **: g_filename_to_uri: assertion `filename != NULL' failed

(rygel:6329): Rygel-CRITICAL **: string_replace: assertion `replacement 0.18.0-1!= NULL' failed
Rygel-Tracker-Message: rygel-tracker-item-factory.vala:66: Using none as upload directory for object.item.imageItem.photo

(rygel:6329): GLib-CRITICAL **: g_filename_to_uri: assertion `filename != NULL' failed
Rygel-Message: New plugin 'Tracker' available
Rygel-Message: New plugin 'Playbin' available
Mediathek-Message: rygel-mediathek-plugin.vala:33: Plugin 'ZDFMediathek' disabled by user, ignoring..
MPRIS-Message: rygel-mpris-plugin-factory.vala:33: Module 'MPRIS' disabled by user. Ign(rygel:6329): Rygel-CRITICAL **: string_replace: assertion `replacement != NULL' failed
Rygel-Tracker-Message: rygel-tracker-item-factory.vala:66: Using none as upload directory for object.item.audioItem.musicTrack

(rygel:6329): GLib-CRITICAL **: g_filename_to_uri: assertion `filename != NULL' failed

(rygel:6329): Rygel-CRITICAL **: string_replace: assertion `replacement != NULL' failed
Rygel-Tracker-Message: rygel-tracker-item-factory.vala:66: Using none as upload directory for object.item.videoItem

(rygel:6329): GLib-CRITICAL **: g_filename_to_uri: assertion `filename != NULL' failed

(rygel:6329): Rygel-CRITICAL **: string_replace: assertion `replacement != NULL' failed
Rygel-Tracker-Message: rygel-tracker-item-factory.vala:66: Using none as upload directory for object.item.imageItem.photo

(rygel:6329): GLib-CRITICAL **: g_filename_to_uri: assertion `filename != NULL' failed
Rygel-Message: New plugin 'Tracker' available(rygel:6329): Rygel-CRITICAL **: string_replace: assertion `replacement != NULL' failed
Rygel-Tracker-Message: rygel-tracker-item-factory.vala:66: Using none as upload directory for object.item.audioItem.musicTrack

(rygel:6329): GLib-CRITICAL **: g_filename_to_uri: assertion `filename != NULL' failed

(rygel:6329): Rygel-CRITICAL **: string_replace: assertion `replacement != NULL' failed
Rygel-Tracker-Message: rygel-tracker-item-factory.vala:66: Using none as upload directory for object.item.videoItem

(rygel:6329): GLib-CRITICAL **: g_filename_to_uri: assertion `filename != NULL' failed

(rygel:6329): Rygel-CRITICAL **: string_replace: assertion `replacement != NULL' failed
Rygel-Tracker-Message: rygel-tracker-item-factory.vala:66: Using none as upload directory for object.item.imageItem.photo

(rygel:6329): GLib-CRITICAL **: g_filename_to_uri: assertion `filename != NULL' failed
Rygel-Message: New plugin 'Tracker' available
Rygel-Message: New plugin 'Playbin' available
Mediathek-Message: rygel-mediathek-plugin.vala:33: Plugin 'ZDFMediathek' disabled by user, ignoring..
MPRIS-Message: rygel-mpris-plugin-factory.vala:33: Module 'MPRIS' disabled by user. Ignoring&#8230;
Rygel-Message: New plugin 'MediaExport' available
External-Message: rygel-external-plugin-factory.vala:33: Module 'External' disabled by user. Ignoring&#8230;
GstLaunch-Message: rygel-gst-launch-plugin.vala:28: Plugin 'GstLaunch' disabled by user, ignoring..

Rygel-Message: New plugin 'Playbin' available
Mediathek-Message: rygel-mediathek-plugin.vala:33: Plugin 'ZDFMediathek' disabled by user, ignoring..
MPRIS-Message: rygel-mpris-plugin-factory.vala:33: Module 'MPRIS' disabled by user. Ignoring&#8230;
Rygel-Message: New plugin 'MediaExport' available
External-Message: rygel-external-plugin-factory.vala:33: Module 'External' disabled by user. Ignoring&#8230;
GstLaunch-Message: rygel-gst-launch-plugin.vala:28: Plugin 'GstLaunch' disabled by user, ignoring..
oring&#8230;
Rygel-Message: New plugin 'MediaExport' available
External-Message: rygel-external-plugin-factory.vala:33: Module 'External' disabled by user. Ignoring&#8230;
GstLaunch-Message: rygel-gst-launch-plugin.vala:28: Plugin 'GstLaunch' disabled by user, ignoring..
oring&#8230;
Rygel-Message: New plugin 'MediaExport' available
External-Message: rygel-external-plugin-factory.vala:33: Module 'External' disabled by user. Ignoring&#8230;
GstLaunch-Message: rygel-gst-launch-plugin.vala:28: Plugin 'GstLaunch' disabled by user, ignoring..

And nothing happens.

---


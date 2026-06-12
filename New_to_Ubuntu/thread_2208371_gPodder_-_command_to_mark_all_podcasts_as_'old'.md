---
title: "gPodder - command to mark all podcasts as 'old'"
date: 2014-02-27
forum: New to Ubuntu
---

### Post by arvindp3 on 2014-02-27
I am using gpodder 3.5.1 under Ubuntu 12.04.  Occasionally I mark all podcast entries as 'old' (or 'not new'). That helps me notice fresh podcasts easily after the next update. I do this from Gpodder GUI front-end by making it show all podcasts (View->All Episodes) and then marking all podcasts as 'not-new' by right-clicking.  

But this process takes time due to large number of podcast entries. Gpodder has a command line interface. Is there a command line option (or script) available to mark all podcasts as 'old'?

---

### Post by tgalati4 on 2014-02-27
You will have to spend some time with this:

Open a terminal:

```
gpo
```

Type help at the gpo> command prompt and you will see a bunch of switches including the *set* command.  I'm not sure what values to use, but play around with it.

I found the set keys:

gpo> set
auto.retries = 3
device_sync.custom_sync_name = {episode.pubdate_prop}_{episode.title}
device_sync.custom_sync_name_enabled = False
device_sync.delete_played_episodes = False
device_sync.device_folder = /media/tgalati4/PHONE CARD/music
device_sync.device_type = filesystem
device_sync.max_filename_length = 999
device_sync.one_folder_per_podcast = True
device_sync.skip_played_episodes = True
extensions.enabled = rm_ogg_cover,notification
flattr.flattr_on_play = False
flattr.token = 
limit.episodes = 200
mygpo.enabled = False
mygpo.password = 
mygpo.server = gpodder.net
mygpo.username = 
player.audio = default
player.video = default
software_update.check_on_startup = False
software_update.interval = 5
software_update.last_check = 0
youtube.preferred_fmt_id = 18
auto.cleanup.days = 7
auto.cleanup.played = False
auto.cleanup.unfinished = True
auto.cleanup.unplayed = False
auto.update.enabled = True
auto.update.frequency = 20
device_sync.after_sync.delete_episodes = False
device_sync.after_sync.mark_episodes_played = True
device_sync.after_sync.sync_disks = False
extensions.rm_ogg_cover.context_menu = True
limit.bandwidth.enabled = False
limit.bandwidth.kbps = 500.0
limit.downloads.concurrent = 1
limit.downloads.enabled = True
mygpo.device.caption = gPodder on Mint14-Extensa
mygpo.device.type = desktop
mygpo.device.uid = Mint14-Extensa
ui.cli.colors = True
ui.gtk.html_shownotes = True
ui.gtk.live_search_delay = 200
ui.gtk.new_episodes = show
ui.gtk.toolbar = False
ui.qml.autorotate = False
ui.gtk.download_list.remove_finished = True
ui.gtk.episode_list.columns = 5
ui.gtk.episode_list.descriptions = True
ui.gtk.episode_list.embed_shownotes = False
ui.gtk.episode_list.view_mode = 1
ui.gtk.podcast_list.all_episodes = True
ui.gtk.podcast_list.hide_empty = False
ui.gtk.podcast_list.sections = True
ui.gtk.podcast_list.view_mode = 1
ui.qml.state.episode_list_filter = 0
ui.gtk.state.episode_selector.height = 400
ui.gtk.state.episode_selector.maximized = False
ui.gtk.state.episode_selector.width = 600
ui.gtk.state.episode_selector.x = 440
ui.gtk.state.episode_selector.y = 140
ui.gtk.state.episode_window.height = 400
ui.gtk.state.episode_window.maximized = False
ui.gtk.state.episode_window.width = 715
ui.gtk.state.episode_window.x = 3
ui.gtk.state.episode_window.y = 24
ui.gtk.state.main_window.height = 500
ui.gtk.state.main_window.maximized = False
ui.gtk.state.main_window.paned_position = 200
ui.gtk.state.main_window.width = 700
ui.gtk.state.main_window.x = 193
ui.gtk.state.main_window.y = 34

Unfortunately, I don't see a key value to set.  So you can look at the database structure--it is open source after all, and devise a script to modify the database directly.  Or, send an email to the developers and ask for a feature addition.  Perhaps others have requested this and it is in the roadmap.

---


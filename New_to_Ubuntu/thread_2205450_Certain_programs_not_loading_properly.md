---
title: "Certain programs not loading properly"
date: 2014-02-13
forum: New to Ubuntu
---

### Post by oozaru on 2014-02-13
I install 13.10 and was having issues with certain programs not loading, just appearing in the launcher. So I went back to 12.04 and I'm still having that problem

---

### Post by deadflowr on 2014-02-13
Any example you could give us on what programs are doing this?

and probably info on your system(machine) wouldn't hurt.

---

### Post by oozaru on 2014-02-14
> **deadflowr said:**
> Any example you could give us on what programs are doing this?

and probably info on your system(machine) wouldn't hurt.

It seems like random programs...

Software Center, Rhythmbox, Musescore, System Monitor

& I'm not sure what system info you want

---

### Post by deadflowr on 2014-02-14
Let's see what the output for one or two of those randomly crashing apps might be.
You can try opening up program via the command line.
try this
open a terminal and try one(or more) of these
```
firefox
```
or
```
software-center
```
or
```
gedit
```
post the output of whatever comes up.

---

### Post by oozaru on 2014-02-14
firefox and gedit both work

software-center outputs ```
2014-02-14 11:26:30,014 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2014-02-14 11:26:30,114 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2014-02-14 11:26:32,594 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2014-02-14 11:26:33,295 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2014-02-14 11:26:33,354 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2014-02-14 11:26:44,007 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/utils.py', 201, 'get_title_from_html')'
2014-02-14 11:26:44,007 - root - WARNING - failed to parse: '<div style="background-color: #161513; width:1680px; height:200px;">
 <div style="background: url('/site_media/exhibits/2013/09/AAMFP_Leaderboard_700x200_1.jpg') top left no-repeat; width:700px; height:200px;"></div>
</div>' ('ascii' codec can't encode character u'\xa0' in position 70: ordinal not in range(128))
2014-02-14 11:26:46,335 - softwarecenter.db.update - INFO - skipping region restricted app: 'Comentarios Web' (not whitelisted)
2014-02-14 11:26:48,205 - softwarecenter.db.update - INFO - skipping region restricted app: 'Flaggame' (not whitelisted)
2014-02-14 11:26:49,017 - softwarecenter.db.update - INFO - skipping region restricted app: 'Bulleti d'esquerra de Calonge i Sant Antoni ' (not whitelisted)
2014-02-14 11:26:49,302 - softwarecenter.db.update - INFO - skipping region restricted app: 'Source Code Analyzer' (not whitelisted)
2014-02-14 11:26:51,600 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
2014-02-14 11:26:51,602 - softwarecenter.db.database - INFO - reopen() database
2014-02-14 11:26:51,602 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
```

---


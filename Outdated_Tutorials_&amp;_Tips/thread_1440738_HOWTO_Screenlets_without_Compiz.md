---
title: "HOWTO: Screenlets without Compiz"
date: 2010-03-27
forum: Outdated Tutorials &amp; Tips
---

### Post by r4z0rw0lf on 2010-03-27
**_[SIZE="4"]Intro[/SIZE]_**
This is a tutorial intended for users that are unable to run Compiz, or have no hardware acceleration(like me :D).
**_[SIZE="4"]Steps[/SIZE]_**
[LIST=1]
**_[SIZE="2"]Get WMctrl[/SIZE]_**
So, first thing you need is [WMctrl]("http://tripie.sweb.cz/utils/wmctrl/"), which is a powerful command line tool, capable of moving windows around to different workspace, resizing, and all that stuff.
```
sudo apt-get install wmctrl
```

**_[SIZE="2"][*]Create the perl script[/SIZE]_**
```
vim ~/Screenlethide.pl
```
Make sure you are in **_I_**nsert mode and paste the following:
```

#!/usr/bin/perl
@window_list = `wmctrl -l | grep "Screenlet.py"`;
foreach my $win (@window_list){
$id=substr $win,0,10;;
$desktop = substr($win,10,3);
if($desktop==0){
  $moveto="1";
}else{
  $moveto="0";
}
system("wmctrl -i -r $id -t $moveto"); 
}

```
save and chmod the file to execute:
```
chmod +x Screenlethide.pl
```
What that script does is take any window whose title ends in "Screenlet.py" and moves it to workspace 1. If its already in that workspace it moves it to workspace 0.
**_[SIZE="2"][*]Add the Shortcut[/SIZE]_**
Now add the shortcut to Gnome(I don't know how to do this in KDE :()
```
gnome-keybinding-properties
```
Click '_A_dd, Name it "Screenlet hide", and put the command as "~/Screenlethide.pl"
Click Apply.
Add a shortcut.
[/LIST]
Let me know if I did anything wrong!:P

---


---
title: "Effectively ejecting media devices with Amarok"
date: 2008-05-01
forum: Outdated Tutorials &amp; Tips
---

### Post by bleaked on 2008-05-01
[SIZE="1"]This is a quick tip that I want to highlight since for the longest time I was having difficulties with Amarok ejecting a media device (iPod) via its disconnect button within the Devices tab.

So, from within the Devices tab, click the 'Configure Device' icon (little blue cogs) which is just to the right of the Connect / Disconnect / Transfer buttons.

Next, set you Post-disconnect command to the following:
```
echo "YOUR USER PASSWORD HERE" | sudo -S eject -m %d
```

Click Ok, then restart Amarok.

From now on, when you click Disconnect, your media device should properly unmount and eject.


Also, apparently for some users this command will not work through the Amarok GUI.  If this is you (likely an older version of Amarok), simply edit the the ~/.kde/share/config/amarokrc configuration file with your favourite text editor, adding the above command to the ' PostDisconnectCommand ' option.

Something like this should work:
```
PostDisconnectCommand=echo "YOUR USER PASSWORD HERE" | sudo -S eject -m %d
```


I have to sincerely thank [TryMe]("http://ubuntuforums.org/member.php?u=6792") here on the forums for this excellent solution.

.:bleaked[/SIZE]

---


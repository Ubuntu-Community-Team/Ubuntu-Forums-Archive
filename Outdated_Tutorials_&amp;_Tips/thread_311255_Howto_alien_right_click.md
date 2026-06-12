---
title: "Howto alien right click"
date: 2006-12-02
forum: Outdated Tutorials &amp; Tips
---

### Post by seiflotfy on 2006-12-02
alien is a program u use to convert .rpm packages to .deb
first make sue you have alien by simply 
```
sudo apt-get install alien
```
then:
```

~/.gnome2/nautilus-scripts/alien-this

```
write:
```
#!/bin/bash
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
# run alien
    	gnome-terminal -x gksudo alien -d ${uri:7}
done
```
close the gedit and type into the terminal
```
 chmod +x ~/.gnome2/nautilus-scripts/alien-this 
 
```
then make it executable
now you are ready to go

---


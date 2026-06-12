---
title: "SystemError: NULL object passed to Py_BuildValue"
date: 2007-02-22
forum: Programming Talk
---

### Post by Malac on 2007-02-22
I'm fairly new to Python and I'm working on the USP project "places" plugin.
I'm trying to get the gnomevfs unmount() to work but I keep getting the following error:
```
SystemError: NULL object passed to Py_BuildValue
```The code is this:

I'm connecting the function with this:```
            self.mTree.get_widget( "UnmountItem" ).connect( "activate", self.UnmountChosen, w, self.mTree)
```And the Function  is this:```
    def UnmountChosen(self, menuitem, button, callingmenu):
        for volume in gnomevfs.VolumeMonitor().get_mounted_volumes():
            if string.replace(string.join(volume.get_activation_uri().split( "//" )[1].split( "%20" ) ),"%23","#") == self.Exec[1]:
                try:
                    volume.unmount( self.UnmountEjectCallback )
                except:
                    print "Unable to Unmount"

    def UnmountEjectCallback(self, *args, **kargs):
        # Do Nothing except return as re-drawing is handled with VolumeMonitor calls
        return
```The unmount is working, I just keep getting the error and I've no idea why or how to rectify it.
Any help greatly appreciated.

---


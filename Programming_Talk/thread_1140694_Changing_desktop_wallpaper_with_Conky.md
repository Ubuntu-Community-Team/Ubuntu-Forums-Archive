---
title: "Changing desktop wallpaper with Conky"
date: 2009-04-27
forum: Programming Talk
---

### Post by Goombie on 2009-04-27
I was wondering if it is possible to create a script (Ruby, Perl, whatever) to do the following things. I would call the script from Conky at a set interval.
I want the script to:
1) Select a desktop wallpaper from one of four different wallpaper lists, depending on the workspace I'm in. The lists would be stored in XML files, in a format like so:
    <workspace name="Nature" no="1">
        <file>/media/Personal Stuff/Pictures/Wallpapers/Nature/1280x800-wallpaper-2.jpg</file>
More files..
    </workspace>
 <workspace name="Foo" no="2">
        <file>/media/Personal Stuff/Pictures/Wallpapers/Nature/01543_falls_1280x800.jpg</file>
More files..
    </workspace>
And so on.
2) Change the wallpaper (in sequential order) at a set interval to another one from that workspace's wallpaper list.
3) Change the wallpaper whenever I switch workspaces to the wallpaper for that workspace. 
Essentially, I'm wondering if it is possible to create a script to duplicate the wallpaper changing function of the program [Wallpapoz.]("http://wallpapoz.akbarhome.com/") I haven't programmed in a long time, so I'm kind of rusty. Any input is appreciated! :D

---


---
title: "Making executables appear in app launcher."
date: 2014-04-12
forum: New to Ubuntu
---

### Post by Andrew_Sunde on 2014-04-12
I have downloaded Minecraft. To run it I select 'open with openJDK java7 runtime' on the Minecarft.jar file in my downlaods folder, and then it opens. In my home folder there is a file named '.minecraft'. How can I get Minecraft to appear in my app launcher. (I'm running elementaryOS).

---

### Post by buzzingrobot on 2014-04-12
Elementary's underpinnings are based on Ubuntu 12.04, but it uses a different application launcher. Probably best to look here: [http://elementaryos.org/support](http://elementaryos.org/support).

---

### Post by grumblebum2 on 2014-04-12
Try this....
[http://elementaryos.org/answers/create-shortcut-of-terminal-commands-in-dock-panel](http://elementaryos.org/answers/create-shortcut-of-terminal-commands-in-dock-panel)
Change the **Exec=** line to reflect your path to minecraft....most likely from your previous post...
```
java -jar /home/[COLOR="#FF0000"]username[/COLOR]/Downloads/minecraft/minecraft.jar lc
```
Change to [COLOR="#FF0000"]your username[/COLOR]. If you go to your minecraft.jar file in the browser then right click on minecraft.jar and select copy. It will copy the path to the clipboard.


You could also try using this as your **~/.local/share/applications/minecraft.desktop** file.
I just now installed minecraft with directions from [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://www.omgubuntu.co.uk/2013/04/minecraft-installer-for-ubuntu")
It installed this .desktop file.
```
[Desktop Entry]
Type=Application
Name=Minecraft
GenericName=Game
Comment=Break and place blocks to build imaginative things
Exec=sh -c "XMODIFIERS= java -Xmx2048M -Xms512M -cp [COLOR="#FF8C00"]/usr/share/minecraft/minecraft.jar[/COLOR] net.minecraft.bootstrap.Bootstrap"
Icon=minecraft
Categories=Game
StartupNotify=true
Actions=Screenshots;Textures;Wiki

[Desktop Action Screenshots]
Name=_Screenshots
Exec=xdg-open .minecraft/screenshots/

[Desktop Action Textures]
Name=_Texture Packs
Exec=xdg-open .minecraft/texturepacks/


[Desktop Action Wiki]
Name=_Wiki
Exec=xdg-open http://www.minecraftwiki.net/
```
Change for [COLOR="#FF8C00"]your path to minecraft.jar[/COLOR]

You can test either of the **Exec=** lines in terminal.

---


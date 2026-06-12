---
title: "[SOLVED] Problem with Java in Eclipse"
date: 2008-09-08
forum: Programming Talk
---

### Post by Fixel on 2008-09-08
Hi, I've used Eclipse previously on another computer and it's worked fine. But on a fresh install it's not working properly.

To test Eclipse I wrote this hello:

```
import javax.swing.*;
public class program {
	public static void main(String[] arg){
		JOptionPane.showMessageDialog(null, "I R Test");
		System.exit(0);
	}
}

```

Nothing fancy just to see if it all worked properly. It launches and the message shows. But I can't press [OK] or the X, so I have to force-quit it.

I get these "errors" in my console:

```
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/menubar-custom.rc:242: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-blue-green.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/menubar-custom.rc:245: Background image options specified without filename
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/menubar-custom.rc:251: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-blue-green.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/menubar-custom.rc:254: Background image options specified without filename
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/toolbar-custom.rc:72: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-blue-green.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/toolbar-custom.rc:75: Background image options specified without filename
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:8: Unable to locate image file in pixmap_path: "Panel/panel-bg-gray-24.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:32: Unable to locate image file in pixmap_path: "Panel/panel-bg-blue-24.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:60: Unable to locate image file in pixmap_path: "Panel/panel-bg-black-24.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:90: Unable to locate image file in pixmap_path: "Panel/panelbutton_gray_2.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:93: Background image options specified without filename
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:100: Unable to locate image file in pixmap_path: "Panel/panelbutton_gray_1.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:103: Background image options specified without filename
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:111: Unable to locate image file in pixmap_path: "Panel/panelbutton_gray_2.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:117: Background image options specified without filename
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:125: Unable to locate image file in pixmap_path: "Panel/panelbutton_gray_4.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:131: Background image options specified without filename
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:138: Unable to locate image file in pixmap_path: "Panel/panelbutton_gray_4.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:141: Background image options specified without filename
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:148: Unable to locate image file in pixmap_path: "Panel/panelbutton_gray_1.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:151: Background image options specified without filename
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:178: Unable to locate image file in pixmap_path: "Panel/panelbutton_black_2.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:181: Background image options specified without filename
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:188: Unable to locate image file in pixmap_path: "Panel/panelbutton_black_1.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:191: Background image options specified without filename
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:199: Unable to locate image file in pixmap_path: "Panel/panelbutton_black_2.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:205: Background image options specified without filename
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:213: Unable to locate image file in pixmap_path: "Panel/panelbutton_black_4.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:219: Background image options specified without filename
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:226: Unable to locate image file in pixmap_path: "Panel/panelbutton_black_4.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:229: Background image options specified without filename
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:236: Unable to locate image file in pixmap_path: "Panel/panelbutton_black_1.png"
/home/fixel/.themes/LiNsta-GTK2/gtk-2.0/panel_custom.rc:239: Background image options specified without filename

```

So I thought it had something to do with compiz/emerald so I tried switching to Metacity/GKT using the fusion-icon. But it still gives me the same errors.

What should I do? I'm pretty lost.

---

### Post by Reiger on 2008-09-08
Considering the weirdness with a bunch of GTK errors, I think the issue lies with your JRE (which I guess is the GNU implementation). You probably can 'fix' it by installing a proper JDK/JRE combo from Sun's; install it like so:

```

$ sudo aptitude install sun-java6-jdk

```
(The $ sign is the prompt.)

Then go to your Eclipse, and make the following changes IIRC:

Window -> Preferences -> Java -> Compiler -> Add JRE;
from the window that pops up:

browse to your /usr/lib/jvm/java-[version_number_here]/jre folder;
select that, you should (soon) see a list of standard libs listed in the appropiate section of the pop-up window.

Apply/OK the changes, click on the checkbox before the new compiler entry in the underlying window pane (this sets the new Java as the default compiler) and try a new project.

---

### Post by Fixel on 2008-09-08
Thanks! Worked like a charm!

---

### Post by The Resident Expert on 2008-09-16
That helped me, too!  :guitar:

---


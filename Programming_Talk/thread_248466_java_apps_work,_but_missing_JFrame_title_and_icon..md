---
title: "java apps work, but missing JFrame title and icon..."
date: 2006-09-01
forum: Programming Talk
---

### Post by _duncan_ on 2006-09-01
Hi. I developed a few apps using sun-java 1.5 sdk running eclipse 3.1 under windows xp. Been trying to transfer these apps to Ubuntu Breezy 5.10. Most of these apps are swing-based.

I have successfully installed jdk1.5 and eclipse 3.1.1. Also configured the system to use sun-java as default (i.e. java, jar, javah, javadoc, etc). All my apps seem to be running correctly, except for one minor glitch:

For whatever reason, JFrame and JOptionPane windows are displayed without the correct frame title, and also without the default sun icon (cup of steaming coffee), even if the .title properties are explicitly set. In some of my apps, I even used custom icons, but these are all ignored in the frame title.

I use the cross-platform look and feel (metal) by default, but switching to CDE or GTK L&Fs doesn't solve the problem.

Is this a bug with the sun-java implementation in Breezy 5.10? Or is there a configuration file I have to edit to make this work?

BTW, I tried 2 ways to install the sun-java SDK: The first using java-package from the repositories, and the second following the method outlined in the wiki. Both worked but with exactly the same problem.

Other info about my sun-j2sdk1.5 installation:
- binary file (jdk-1_5_0_07-linux-i586.bin) downloaded from Sun website.
- packaged into <deb file> using java-package version 0.26.
- installed using dpkg -i <deb file>.
- system configured to use sun-java by default: sudo update-alternatives --config java (also jar, javah, javadoc, etc.)

---

### Post by kaamos on 2006-09-01
> For whatever reason, JFrame and JOptionPane windows are displayed without the correct frame title, and also without the default sun icon

Frame titles have always worked, but I have actually never seen the cup logo in linux.

> In some of my apps, I even used custom icons, but these are all ignored in the frame title.

How do you set the icon? Have you checked that it isn't just a problem with eclipse by using an absolute path to the icon
```

	JFrame mainWindow = new JFrame("This is a window");
	ImageIcon icon = new ImageIcon("/usr/share/icons/Tango/24x24/apps/terminal.png");
	mainWindow.setIconImage(icon.getImage());

```

---

### Post by _duncan_ on 2006-09-01
> **kaamos said:**
> How do you set the icon? Have you checked that it isn't just a problem with eclipse by using an absolute path to the icon

Thank you for the response. I'm quite sure it's not just a problem with eclipse since even jar files launched from the command line using java -jar <package name> shows the same problem. Even demo jar files that came with the SDK manifest the same problem when launched from the command line.

Also, it's probably not a relative/absolute path problem since customized icons inside the JFrame (e.g. JMenuItem, JButton, JLabel, etc) are all displayed correctly.

I can live without the customized icons on the title bar, but not having the text title shown is the bigger problem for me, I plan to open-source some of these apps in the future, and having a title-less app window can be confusing for potential end-users.

As a final test, I wrote a very simple program that contains only one functional line inside the main class:
```
import javax.swing.JOptionPane;

public static void main(String[] args) {
    JOptionPane.showMessageDialog(
            null,
            "This is a test",
            "Test Title",
            JOptionPane.ERROR_MESSAGE
    );
}
```
I compiled the program, quit Eclipse, then run using a terminal. The JOptionPane showed up, everything inside the panel were displayed correctly (the text "This is a test" and the default ERROR_MESSAGE icon), but the text "Test Title" is missing from the title bar.

Just to rule out Eclipse as the source of the problem, I also compiled the same .java file using the command line, but with the same problem.

---

### Post by rus on 2006-10-20
I have the same problem. No JFrame titles. Who know solution?
Thanks in advance.

---

### Post by _duncan_ on 2006-10-20
I was able to resolve the problem, but not entirely sure what I did exactly to make it work.

1. Changed the default language for Ubuntu 6.06 from "English (Philippines)" to "English (United States of America)". This was after seeing some earlier bug reports at the Sun Java website about unsupported locales. I used the gnome desktop GUI to do this: System > Administration > Language Support.

At first, it didn't seem to work. My JDialogs and JFrames were still without titles.

2. I added 2 lines to my main class just before invoking JOptionPane (pls. refer to my earlier test code):

```

JDialog.setDefaultLookAndFeelDecorated(true);
JFrame.setDefaultLookAndFeelDecorated(true);

```

My frame's style was changed from the default metal L&F to decorated, and the title was displayed. I wasn't at all happy with this workaround but at least my applications now have titles!

What's weird is that a few days later, other java apps I didn't write (e.g. Limewire, Azureus, Compiere) started running with titles already, even with the default metal L&F. So, on a hunch, I removed the 2 lines in #2 from my code, and my own java apps started showing titles in the default metal L&F.

My suggestion is to try #1 first, then reboot. See if it works. If not, try #2. If it still doesn't work, I don't know anymore.

---

### Post by rus on 2006-10-21
Only 1. works! Thank you Duncan. What is interesting that Russian titles become visible too. Nevertheless this is obviously a bug because my default language is Russian and my users would'nt be very happy to switch a hole desktop to run java apps :( Don't you know, by the way, where to report such bugs?
Thank you once more.

---

### Post by _duncan_ on 2006-10-21
You are welcome.

I don't know where to report the bug, but maybe it's better to wait for the release of Java 6. I understand a lot of these issues with Gnome/GTK will be addressed by this new version.

If not, I'll probably switch over to SWT for future GUI design instead of Swing.

---


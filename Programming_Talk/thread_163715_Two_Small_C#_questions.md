---
title: "Two Small C# questions"
date: 2006-04-21
forum: Programming Talk
---

### Post by Kimm on 2006-04-21
I just have two small questions, as I am pretty new to C# and GTK#

I'm writing an app that I will then place on a CD along with every data file and picture/video/song that has something to do with my class to hand out on our final day of school.
The App will start when the CD is put in the drive (atleast in windows) and it will be written in C# so that it will run pretty much anywhere, I have alredy started writing the app.

I want to print the OS the app is running on to a label, and I tried doing
```

Label lbl1 = new Label(System.SystemID.GetName)

```
but the compiler complaints about types.

I also want to know in what directory the app is running, so that I can load images and such.
I tried just entering the name of the image file (that was in the same dir as the app), Mono didnt like that and I have to write the full path, obviosly then .NET on windows wount be happy...

Any help apretiated! but please no referals to python, I'm better and C/C++ like languages and hardly know Python at all, I allredy considerd it for this project but came to the conclution that that would need more work.

---

### Post by DeadEyes on 2006-04-21
```

Environment.CurrentDirectory

```
I think returns the directory that the process was started in.
Don't know about any of the other bits.

---

### Post by mostwanted on 2006-04-21
[QUOTE=Kimm]I just have two small questions, as I am pretty new to C# and GTK#

I'm writing an app that I will then place on a CD along with every data file and picture/video/song that has something to do with my class to hand out on our final day of school.
The App will start when the CD is put in the drive (atleast in windows) and it will be written in C# so that it will run pretty much anywhere, I have alredy started writing the app.

I want to print the OS the app is running on to a label, and I tried doing
```

Label lbl1 = new Label(System.SystemID.GetName)

```
but the compiler complaints about types.

I also want to know in what directory the app is running, so that I can load images and such.
I tried just entering the name of the image file (that was in the same dir as the app), Mono didnt like that and I have to write the full path, obviosly then .NET on windows wount be happy...

Any help apretiated! but please no referals to python, I'm better and C/C++ like languages and hardly know Python at all, I allredy considerd it for this project but came to the conclution that that would need more work.[/QUOTE]

First of all: GIVE US THE DAMN ERROR! How can we possible help if you don't tell us what the error message is ](*,)

Second, looking through the Mono documentation I couldn't find your System.SystemID.GetName method ([http://www.go-mono.com/docs/)](http://www.go-mono.com/docs/)). I'm left wondering if that could have something to do with the error you're getting.

You also realise that your class-mates will have to install Mono or .NET+Gtk# to run the app? Should include those on the disc.

---

### Post by Kimm on 2006-04-21
Sorry, it wasnt "System.SystemID.GetName" it was "System.PlatformID.GetName"
As I said, the error had to do with incompatible types, I thought that would be sufficient, but this is the full error-message anyway:

"Cannot convert method group `GetName' to non-delegate type `string'. Did you intend to invoke the method?(CS0428)"

Allthough that doesnt mather anymore, DeadEyes suggestion lead me to find out how to print the OS aswell by doing "Environment.OSVersion", it detects my system as "Unix 2.6.15.6" though, but that doesnt realy mather.

> 
You also realise that your class-mates will have to install Mono or .NET+Gtk# to run the app? Should include those on the disc.


Well yes, I was planning on having a C++ terminal app start and look for .NET and GTK# before strarting the real thing. I pretty much assume that most people have .NET installed on their computers by now though, especialy since everyone around here have high-speed optical internet connections. I think the need to install GTK# is a small price to pay if you want a multi-platform application, I mean... this app will run on pretty much any OS, including OS X, so I am willing to do that. But as you say GTK# will be included on the disk.

---

### Post by LordHunter317 on 2006-04-21
[QUOTE=Kimm]Sorry, it wasnt "System.SystemID.GetName" it was "System.PlatformID.GetName"
As I said, the error had to do with incompatible types, I thought that would be sufficient, but this is the full error-message anyway:

"Cannot convert method group `GetName' to non-delegate type `string'. Did you intend to invoke the method?(CS0428)"[/quote]The error means exactly what it says.  You didn't call the method.  Method calls in C#, even to methods taking no parmeters, require ().

You probably thought it was a property, but as a rule, MS never names properties starting with a verb.

---

### Post by Kimm on 2006-04-22
> You probably thought it was a property, but as a rule, MS never names properties starting with a verb.

So I did, and I'll remember that last part.

I'm suprised at how easy it was to get the app running in both windows and Linux, I just installed GTK# on my fathers winXP computer for experimentational purposes and it runns smoothly.

(note: this isnt the acctual app... just an experiment)

Ubuntu:
[[IMG]http://img101.imageshack.us/img101/3474/expunix8vw.th.png[/IMG]](http://img101.imageshack.us/my.php?image=expunix8vw.png)

Windows:
[[IMG]http://img101.imageshack.us/img101/3585/expwindows3ay.th.png[/IMG]](http://img101.imageshack.us/my.php?image=expwindows3ay.png)

---

### Post by mostwanted on 2006-04-22
[QUOTE=Kimm]So I did, and I'll remember that last part.

I'm suprised at how easy it was to get the app running in both windows and Linux, I just installed GTK# on my fathers winXP computer for experimentational purposes and it runns smoothly.

(note: this isnt the acctual app... just an experiment)

Ubuntu:
[[IMG]http://img101.imageshack.us/img101/3474/expunix8vw.th.png[/IMG]](http://img101.imageshack.us/my.php?image=expunix8vw.png)

Windows:
[[IMG]http://img101.imageshack.us/img101/3585/expwindows3ay.th.png[/IMG]](http://img101.imageshack.us/my.php?image=expwindows3ay.png)[/QUOTE]

Indeed. Gtk# is not as portable as Java on the desktop, but it's very good.

The problem with programming on Mono is that various UNIX tools are available (like i18n for multiple language support or bindings to Gnome-specific tools) which you'll want to use for many apps or the typical UNIX file system layouts (absolute paths preferred over relative), but you won't be able to program this way because it would break cross-platform compatibility. This is why Banshee, Muine, Monodevelop, Beagle, F-Spot and so on are only available for BSD/Linux/OpenSolaris, not OSX and Windows.

---

### Post by Kimm on 2006-04-22
So I just startedd working on the acctual GUI, so far I have managed to get it somewhat like I want it (not to familliar to boxes yet).
I was woundering if I can change the Font Size of Labels? and perhaps add colored areas.

I would like the top to be green, and the text to be much larger.
I also want the text just above the horizontal separator to be larger... that will contain quotes from classmates randomly selected at startup.

[[IMG]http://img71.imageshack.us/img71/9633/guistart2el.th.png[/IMG]](http://img71.imageshack.us/my.php?image=guistart2el.png)

if you want to see the current code, here it is. It doesnt do much besides build a GUI and close the program...

```

using System;
using Gtk;

public class MyWindow : Window
{	
	public MyWindow () : base ("IDCP v0.1 alpha1")
	{
		//declarations:			
		VBox box_main = new VBox(false, 2); //huvudbox
			VBox box_top = new VBox(false, 2); //toppbox
				Label title = new Label("IDCP - Running on " + Environment.OSVersion); //titel
			HBox box_mittle = new HBox(false, 2); //mittbox
				VBox box_loggo = new VBox(false, 2); //loggobox
					Image img_loggo = new Image(Environment.CurrentDirectory + "/Loggo.png");
					Label quote = new Label("Sitat skall vara här!"); //sitat
				VBox box_funkt = new VBox(false, 2); //knappbox
					Button btn_images = new Button("Bilder"); //bilder
					Button btn_videos = new Button("Video"); //video
					Button btn_music = new Button("Musik & Ljud"); //audio
					Button btn_misc = new Button("Diverse Annat"); //diverse
			HSeparator separator = new HSeparator();
			HBox box_system = new HBox(true, 2);
				Button btn_about = new Button("Om Programmet");
				Button btn_exit = new Button("Avsluta Programmet");
				
		//Main packing:
		box_main.PackStart(box_top, false, true, 0);
		box_main.PackStart(box_mittle, true, true, 0);
		box_main.PackStart(separator, false, true, 0);
		box_main.PackStart(box_system, false, true, 0);
	
			//Top packing:
			box_top.PackStart(title, false, false, 0);
				
			//Mittle packing:
			box_mittle.PackStart(box_loggo, true, true, 0);
			box_mittle.PackStart(box_funkt, true, true, 0);
			
				//Loggo packing:
				box_loggo.PackStart(img_loggo, true, true, 0);
				box_loggo.PackStart(quote, false, true, 0);
				
				//Function packing:
				box_funkt.PackStart(btn_images, true, true, 0);
				box_funkt.PackStart(btn_videos, true, true, 0);
				box_funkt.PackStart(btn_music, true, true, 0);
				box_funkt.PackStart(btn_misc, true, true, 0);
			
			//System packing:
			box_system.PackStart(btn_about, false, true, 0);
			box_system.PackStart(btn_exit, false, true, 0);
	
		//events:
			btn_exit.Clicked += new EventHandler(exit);
	
		this.SetDefaultSize (700, 500);
		this.DeleteEvent += new DeleteEventHandler (OnMyWindowDelete);
		this.Add(box_main);
		this.ShowAll ();
	}
		
	static void exit(object obj, EventArgs args)
	{
		Application.Quit();
	}
		
	void OnMyWindowDelete (object sender, DeleteEventArgs a)
	{
		Application.Quit ();
		a.RetVal = true;
	}
}

```

---

### Post by mostwanted on 2006-04-22
I'm not an expert on making GUIs, but I think Pango is used for messing with fonts. Try looking it up in the Mono Documentation.

---


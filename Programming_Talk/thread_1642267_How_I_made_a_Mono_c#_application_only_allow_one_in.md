---
title: "How I made a Mono c# application only allow one instance at a time"
date: 2010-12-10
forum: Programming Talk
---

### Post by Rezista on 2010-12-10
Hi all,
First post here, thought I'd post the following info here in case other people needed some ideas...

I use gnome-rdp as an app to manage and connect to the various SSH and RDP servers at work. I set up a keyboard shortcut to launch it when I needed to use it and gnome-rdp has a nice feature where it sits in your panel in case you want to use it again. Problem with using the hotkey was that it would launch a new instance, clogging up your panel after a while.

I downloaded the source and added some simple DBus code. I did this for 2 reasons

1. Easy way to check if a copy is already running
2. Send the gnome-rdp instance in DBus a message telling the UI to show

First I created a simple interface 
```

using System;
namespace GnomeRDP
{
    [NDesk.DBus.Interface ("org.ndesk.Demo")]
    public interface IGnomeRdpServer
    {
        void showUI();
    }
}

```Then i changed the main.cs class. I got it to implement the IGnomeRdpServer interface and added the following method
```

        public void showUI(){
            wndMain.Visible = true;
        }

```Last thing was adding the following code to the main method in Main.cs
```

using NDesk.DBus;
using org.freedesktop.DBus;
...
        private bool dBusDisposed = false;
        private static readonly ObjectPath rootPath = new ObjectPath("/net/sourceforge/gnomerdp");
        private static string busName = "net.sourceforge.gnomerdp";
        
        public static void Main(string[] args)
        {
            new MainApp(args);
        }    

        public MainApp(string[] args) 
        {
            BusG.Init ();
            try{
                Console.WriteLine("about to register dbus");    
                var bus = Bus.Session;
                if (bus.RequestName(busName, NameFlag.ReplaceExisting & NameFlag.AllowReplacement & NameFlag.DoNotQueue) != RequestNameReply.PrimaryOwner)
                {
//we get here if there's an existing instance already registered in DBus
                        Console.WriteLine("checking for existing instance");    
                        IGnomeRdpServer rdp = Bus.Session.GetObject<IGnomeRdpServer>(busName, rootPath);
                        rdp.showUI();
                        Console.WriteLine("found and focussing done");    
                        return;
                }
                bus.Register(rootPath, this);
                Console.WriteLine("DBus server registered.");
            } catch (Exception ex){
                if (ex.Message.StartsWith("org.freedesktop.DBus.Error.ServiceUnknown")){
                    Console.WriteLine("not found");    
                } else {
                    Console.WriteLine(ex.ToString());
                    return;
                }
            }
// do the rest
}
....
//somewhere in the OnQuit method
        private bool OnQuit()
                if (!dBusDisposed){
                    Console.WriteLine("about to de-register dbus");
                    var bus = Bus.Session;
                    bus.Unregister(rootPath);
                    Console.WriteLine("de-register dbus done");
                }
}



```Code isn't the prettiest but it serves its purpose!

---

### Post by directhex on 2010-12-10
> **Rezista said:**
> Hi all,
First post here, thought I'd post the following info here in case other people needed some ideas...

I use gnome-rdp as an app to manage and connect to the various SSH and RDP servers at work. I set up a keyboard shortcut to launch it when I needed to use it and gnome-rdp has a nice feature where it sits in your panel in case you want to use it again. Problem with using the hotkey was that it would launch a new instance, clogging up your panel after a while.

I downloaded the source and added some simple DBus code. I did this for 2 reasons

1. Easy way to check if a copy is already running
2. Send the gnome-rdp instance in DBus a message telling the UI to show

First I created a simple interface 
```

using System;
namespace GnomeRDP
{
    [NDesk.DBus.Interface ("org.ndesk.Demo")]
    public interface IGnomeRdpServer
    {
        void showUI();
    }
}

```Then i changed the main.cs class. I got it to implement the IGnomeRdpServer interface and added the following method
```

        public void showUI(){
            wndMain.Visible = true;
        }

```Last thing was adding the following code to the main method in Main.cs
```

using NDesk.DBus;
using org.freedesktop.DBus;
...
        private bool dBusDisposed = false;
        private static readonly ObjectPath rootPath = new ObjectPath("/net/sourceforge/gnomerdp");
        private static string busName = "net.sourceforge.gnomerdp";
        
        public static void Main(string[] args)
        {
            new MainApp(args);
        }    

        public MainApp(string[] args) 
        {
            BusG.Init ();
            try{
                Console.WriteLine("about to register dbus");    
                var bus = Bus.Session;
                if (bus.RequestName(busName, NameFlag.ReplaceExisting & NameFlag.AllowReplacement & NameFlag.DoNotQueue) != RequestNameReply.PrimaryOwner)
                {
//we get here if there's an existing instance already registered in DBus
                        Console.WriteLine("checking for existing instance");    
                        IGnomeRdpServer rdp = Bus.Session.GetObject<IGnomeRdpServer>(busName, rootPath);
                        rdp.showUI();
                        Console.WriteLine("found and focussing done");    
                        return;
                }
                bus.Register(rootPath, this);
                Console.WriteLine("DBus server registered.");
            } catch (Exception ex){
                if (ex.Message.StartsWith("org.freedesktop.DBus.Error.ServiceUnknown")){
                    Console.WriteLine("not found");    
                } else {
                    Console.WriteLine(ex.ToString());
                    return;
                }
            }
// do the rest
}
....
//somewhere in the OnQuit method
        private bool OnQuit()
                if (!dBusDisposed){
                    Console.WriteLine("about to de-register dbus");
                    var bus = Bus.Session;
                    bus.Unregister(rootPath);
                    Console.WriteLine("de-register dbus done");
                }
}



```Code isn't the prettiest but it serves its purpose!

This is pretty cool. Have you sent this as a bug against upstream gnome-rdp? It might also interest people on the mono-devel mailing list.

---

### Post by Rezista on 2010-12-10
No I haven't sent it anywhere else. This is the first place I wrote about it after i got it working. The latest version of gnome-rdp has a DBus service in it and it's where I got some ideas from. However I did this on version 0.2.3 because 0.3 doesn't work in Ubuntu.

---

### Post by GeoMX on 2011-09-22
I'm trying to setup a single instance application in C#, I used Monodevelop to create a new Gtk# 2.0 project and then added your code to it. However, I'm not able to call the **showUI** function for the already running instance, the program gets stuck at **rdp.showUI()**. If I close the first application, the second one finishes throwing a NoReply exception (shouldn't it be catched by the try-catch block?):

```
System.Exception: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
  at OneInstance.IGnomeRdpServerProxy.showUI () [0x00000] 
  at OneInstance.MainClass.Main (System.String[] args) [0x0005a] in Main.cs:28 
```

I have three source files in the project, this is the content:

IGnomeRdpServer.cs:
```

using System;

namespace OneInstance
{
	[NDesk.DBus.Interface( "org.ndesk.Demo" )]
	public interface IGnomeRdpServer
	{
		void showUI();
	}
}

```

Main.cs:
```


using System;
using Gtk;
using NDesk.DBus;
using org.freedesktop.DBus;

namespace OneInstance
{
	class MainClass : IGnomeRdpServer
	{
		private static readonly ObjectPath rootPath = new ObjectPath( "/net/sourceforge/gnomerdp" );
		private static string busName = "net.sourceforge.gnomerdp";
		static MainWindow win;

		public static void Main (string[] args)
		{
			Application.Init ();
			win = new MainWindow ();

			try
			{
				Console.WriteLine( "about to register dbus" );
				var bus = Bus.Session;
				if ( bus.RequestName( busName, NameFlag.ReplaceExisting & NameFlag.AllowReplacement & NameFlag.DoNotQueue ) != RequestNameReply.PrimaryOwner )
				{
					Console.WriteLine( "checking for existing instance" );
					OneInstance.IGnomeRdpServer rdp = Bus.Session.GetObject< OneInstance.IGnomeRdpServer >(busName, rootPath );
					Console.WriteLine( "calling showUI" );
					rdp.showUI();
					Console.WriteLine( "found and focusing done" );
					return;
				}
				bus.Register( rootPath, win );
				Console.WriteLine( "Dbus server registered." );
			}
			catch( Exception ex )
			{
				if ( ex.Message.StartsWith( "org.freedesktop.Dbus.Error.ServiceUnknown" ) )
				{
					Console.WriteLine( "not found" );
				}
				else
				{
					Console.WriteLine( ex.ToString() );
					return;
				}
			}

			win.Show ();
			Application.Run ();
		}
		
		public void showUI()
		{
			win.Visible = true;
		}
	}
}

```

MainWindow.cs:
```

using System;
using Gtk;
using NDesk.DBus;
using org.freedesktop.DBus;

namespace OneInstance
{
public partial class MainWindow : Gtk.Window, IGnomeRdpServer
{
	private bool dBusDisposed = false;
	private static readonly ObjectPath rootPath = new ObjectPath( "/net/sourceforge/gnomerdp" );

	StatusIcon tray;
	
	public MainWindow () : base(Gtk.WindowType.Toplevel)
	{
		Build ();
		this.Visible = false;

		tray = new StatusIcon( new Gdk.Pixbuf( "icon.png" ) );
		tray.Visible = true;
		tray.Activate += delegate { this.Visible = !this.Visible; };
		tray.Tooltip = "Status Icon";
	}

	protected void OnDeleteEvent (object sender, DeleteEventArgs a)
	{
		if ( !dBusDisposed )
		{
			Console.WriteLine( "about to de-register dbus" );
			var bus = Bus.Session;
			bus.Unregister( rootPath );
			Console.WriteLine( "de-register dbus done" );
		}
		Application.Quit ();
		a.RetVal = true;
	}
	
	public void showUI()
	{
		this.Visible = true;
	}
}
}

```
As you can see, I implemented the IGnomeRdpServer interface in both Main and MainWindow classes, it was because when trying the code I also got some errors refering to a non found method showUI in the interface.

Thanks in advance for your help.
-----------------------------------
Edit:

Oh, my. I forgot the call to BusG.Init() ](*,).
Sorry for bothering you folks.

---

### Post by Rezista on 2011-09-23
So it works OK now?

---

### Post by GeoMX on 2011-10-08
Yes, it is working perfect now. Thanks a lot for this tip :).

---


---
title: "Banshee problems"
date: 2011-07-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by CaptainMark on 2011-07-18
Dont know if its a banshee issue alone or oneiric related but banshee has been crashing randomly these past few days, it sometimes wont start at all, trying through a terminal gives me this```
mark@desktop:~$ banshee
[Info  20:13:27.065] Running Banshee 2.1.0: [Ubuntu oneiric (development branch) (linux-gnu, x86_64) @ 2011-07-13 10:41:18 UTC]
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ArgumentException: Value does not fall within the expected range.
  at Hyena.Gui.Canvas.Rect.set_Height (Double value) [0x00000] in <filename unknown>:0 
  at Hyena.Gui.Canvas.Rect.op_Explicit (Rectangle rect) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Gui.ListView`1[Banshee.Collection.AlbumInfo].OnSizeAllocated (Rectangle allocation) [0x00000] in <filename unknown>:0 
  at Gtk.Widget.sizeallocated_cb (IntPtr widget, IntPtr allocation) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.sizeallocated_cb(IntPtr widget, IntPtr allocation)
   at Gtk.Widget.gtksharp_widget_base_show(IntPtr )
   at Gtk.Widget.OnShown()
   at Nereid.PlayerInterface.OnShown()
   at Gtk.Widget.shown_cb(IntPtr widget)
   at Gtk.Widget.gtk_widget_show(IntPtr )
   at Gtk.Widget.Show()
   at Banshee.Gui.BaseClientWindow.InitialShowPresent()
   at Nereid.PlayerInterface.Initialize()
   at Banshee.Gui.BaseClientWindow.InitializeWindow()
   at Banshee.Gui.BaseClientWindow..ctor(System.String title, System.String configNameSpace, Int32 defaultWidth, Int32 defaultHeight)
   at Nereid.PlayerInterface..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Reflection.MonoCMethod , System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Banshee.ServiceStack.ServiceManager.RegisterService(System.Type type)
   at Banshee.ServiceStack.ServiceManager.Run()
   at Banshee.ServiceStack.Application.Run()
   at Banshee.Gui.GtkBaseClient.Initialize(Boolean registerCommonServices)
   at Banshee.Gui.GtkBaseClient..ctor(Boolean initializeDefault, System.String defaultIconName)
   at Banshee.Gui.GtkBaseClient..ctor()
   at Nereid.Client..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Reflection.MonoCMethod , System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.AppDomain , System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()

```anyone else having this issue, if its not just me ill log a launchpad bug report

---

### Post by MacUntu on 2011-07-18
Are you using the daily PPA?

---

### Post by mc4man on 2011-07-18
Banshee (repo package) works fine here with the exception that they seem to be dragging their feet fixing the audio cd breakage (MusicBrainz
Sorta surprising because there has been a simple fix for many weeks - 6 line patch and it works fine
Screen shows patched current O source

Noticed a similar error bug on LP, happens at random (natty), but marked imcomplete for lack of follow up - while it did suggest trying a ppa build I believe the O version is more current

---

### Post by MacUntu on 2011-07-18
Yes, it is. The version from the daily PPA was broken for me. "Down"graded to Oneiric packages and it works fine.

---

### Post by CaptainMark on 2011-07-18
No im not using banshee ppa since changing to oneiric, this is the 11.10 default

---

### Post by lidex on 2011-07-18
Maybe running in debug mode will show something useful:
```
banshee --debug
```

Seem to be a lot of similar issues on these forums. Some fixes include removing extensions, running without dbus, removing configurations here ~/.config/banshee-1/ and here ~/.gconf/apps/banshee-1/

---

### Post by VinDSL on 2011-07-19
> **CaptainMark said:**
> Dont know if its a banshee issue alone or oneiric related but banshee has been crashing randomly these past few days, it sometimes wont start at all [...]

[...]anyone else having this issue, if its not just me ill log a launchpad bug report
Yeah, Banshee has been crashing for me, too.

Actually, 2 days ago, I switched back to Rhythmbox.

Rhythmbox sucks, especially since the devs did away with the rhythmbox-client feature, but at least it gimps along, whistling tunes in the dark.

Banshee trumps Rhythmbox, but the choice is: a poke in the eye with a sharp stick, opposed to a smack on the back of the head with a closed fist.

IMO, there as sooo many bugs in these players (Banshee & Rhythmbox alike) that you're wasting your time reporting yet another bug.

It's best to just ride out the storm...

---

### Post by CaptainMark on 2011-07-19
its completely knackered for me now, i cant run banshee at all for two days and typing banshee in a terminal produces..... nothing, no music no errors, nothing at all,

---

### Post by Quackers on 2011-07-19
I just tried Banshee and it was fine :-)
Then it crashed :-)  oops

---

### Post by CaptainMark on 2011-07-19
seems quite common at the mo, damn ive just got  a new cd i wanna put on my ipod

---

### Post by master_b on 2011-07-22
Try Guayadeque - works perfectly for me - I love its integration of Shoutcast.

---


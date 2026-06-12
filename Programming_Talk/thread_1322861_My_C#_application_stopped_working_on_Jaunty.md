---
title: "My C# application stopped working on Jaunty"
date: 2009-11-11
forum: Programming Talk
---

### Post by kissg1988 on 2009-11-11
I've been developing a C# application, which used to run on Hardy, but suddenly stopped working on Jaunty and Karmic. The issue seems to be related to the GTK libraries, but I still haven't figured out what causes this behaviour.

After starting the application, its main window starts to draw, then suddenly it fades away and an exception is thrown. According to the exception, it seems to be a problem with a native library, namely libgtk-x11-2.0.so or probably libgdk-x11-2.0.so. Using GTK version 2.12.9, which worked flawlessly on Hardy, solves the problem, but another two comes...

What can I do to make my application run on Jaunty and Karmic? Could this be a bug in the GTK libraries?

For reference, here is the source of the Main method:

```

public static void Main (string[] args)
		{
			Application.Init ();
			// Felbontás ellen&#337;rzése
			System.Drawing.Size screensize = System.Windows.Forms.SystemInformation.PrimaryMonitorSize;
			if(screensize.Width<800)
				PopupDialog.ShowErrorMessage("Hiba","A Számlasegéd használatához legalább 800x600-as képerny&#337;felbontás szükséges. Állítsa be a felbontást a megfelel&#337; m&#369;ködés érdekében.");
			MainWindow win = new MainWindow ();
			win.Show ();
			Application.Run();
		}

```

Code from gui.stetic:

```

<widget class="Gtk.Window" id="Számlasegéd.MainWindow" design-size="800 624">
    <action-group name="Default">
      <action id="MveletekAction">
        <property name="Type">Action</property>
        <property name="Label" translatable="yes">_M&#369;veletek</property>
        <property name="ShortLabel" translatable="yes">M&#369;veletek</property>
      </action>
      <action id="BelltsokAction">
        <property name="Type">Action</property>
        <property name="Label" translatable="yes">_Beállítások</property>
        <property name="ShortLabel" translatable="yes">Szerkesztés</property>
      </action>
      <action id="Nzet">
        <property name="Type">Action</property>
        <property name="Label" translatable="yes">_Nézet</property>
        <property name="ShortLabel" translatable="yes">Nézet</property>
      </action>
      <action id="Sg">
        <property name="Type">Action</property>
        <property name="Label" translatable="yes">_Súgó</property>
        <property name="ShortLabel" translatable="yes">Súgó</property>
      </action>
      <action id="jSzmlaKilltsaAction">
        <property name="Type">Action</property>
        <property name="Label" translatable="yes">Ú_j számla kiállítása</property>
        <property name="ShortLabel" translatable="yes">Új számla kiállítása...</property>
        <property name="StockId">gtk-new</property>
        <signal name="Activated" handler="OnUjszamla" />
      </action>
      <action id="gyfladatbzisMegnyitsaAction">
        <property name="Type">Action</property>
        <property name="Accelerator">&lt;Control&gt;&lt;Mod2&gt;g</property>
        <property name="Label" translatable="yes">Ü_gyféladatbázis megnyitása</property>
        <property name="ShortLabel" translatable="yes">Ügyféladatbázis megnyitása</property>
        <property name="StockId">gtk-orientation-portrait</property>
        <signal name="Activated" handler="OnGyfladatbzisMegnyitsaActivated" />
      </action>
      <action id="KszletadatbzisMegnyitsaAction">
        <property name="Type">Action</property>
        <property name="Accelerator">&lt;Control&gt;&lt;Mod2&gt;k</property>
        <property name="Label" translatable="yes">Kész_letadatbázis megnyitása</property>
        <property name="ShortLabel" translatable="yes">Készletadatbázis megnyitása</property>
        <property name="StockId">gtk-preferences</property>
        <signal name="Activated" handler="OnKszletadatbzisMegnyitsaActivated" />
      </action>
      <action id="AdatbzisMentseAction">
        <property name="Type">Action</property>
        <property name="Accelerator">&lt;Mod2&gt;F2</property>
        <property name="Label" translatable="yes">Adatbázis _mentése</property>
        <property name="ShortLabel" translatable="yes">Adatbázis mentése...</property>
        <property name="StockId">gtk-save-as</property>
        <signal name="Activated" handler="OnAdatbzisMentseActivated" />
      </action>
      <action id="AdatbzisVisszalltsaAction">
        <property name="Type">Action</property>
        <property name="Accelerator">&lt;Mod2&gt;F3</property>
        <property name="Label" translatable="yes">Adatbázis _visszaállítása</property>
        <property name="ShortLabel" translatable="yes">Adatbázis visszaállítása...</property>
        <property name="StockId">gtk-refresh</property>
        <signal name="Activated" handler="OnAdatbzisVisszalltsaActivated" />
      </action>
      <action id="KilpsASzmlasegdblAction">
        <property name="Type">Action</property>
        <property name="Label" translatable="yes">_Kilépés a Számlasegédb&#337;l</property>
        <property name="ShortLabel" translatable="yes">Kilépés a Számlasegédb&#337;l</property>
        <property name="StockId">gtk-quit</property>
        <signal name="Activated" handler="OnKilpsASzmlasegdblActionActivated" />
      </action>
      <action id="Msols">
        <property name="Type">Action</property>
        <property name="Label" translatable="yes">Másolás</property>
        <property name="ShortLabel" translatable="yes">Másolás</property>
        <property name="StockId">gtk-copy</property>
      </action>
      <action id="BelltsokSzerkesztse">
        <property name="Type">Action</property>
        <property name="Label" translatable="yes">Beállítások</property>
        <property name="ShortLabel" translatable="yes">Beállítások szerkesztése...</property>
        <property name="StockId">gtk-preferences</property>
      </action>
      <action id="PrograminformcikAction">
        <property name="Type">Action</property>
        <property name="Label" translatable="yes">_Programinformációk</property>
        <property name="ShortLabel" translatable="yes">Információk a programról...</property>
        <property name="StockId">gtk-dialog-info</property>
        <signal name="Activated" handler="infoBoxOpen" />
      </action>
      <action id="FelhasznliDokumentciAction">
        <property name="Type">Action</property>
        <property name="Accelerator">&lt;Mod2&gt;F1</property>
        <property name="Label" translatable="yes">_Felhasználói dokumentáció</property>
        <property name="ShortLabel" translatable="yes">Felhasználói dokumentáció...</property>
        <property name="StockId">gtk-help</property>
        <signal name="Activated" handler="OnFelhasznliDokumentciActivated" />
      </action>
      <action id="Cginformcik">
        <property name="Type">Action</property>
        <property name="Label" translatable="yes">_Cégadatok</property>
        <property name="ShortLabel" translatable="yes">Céginformációk...</property>
        <property name="StockId">gtk-about</property>
        <signal name="Activated" handler="OnCginformcikActivated" />
      </action>
      <action id="KapcsoldsAzAdatbzishoz">
        <property name="Type">Action</property>
        <property name="Label" translatable="yes">Kapcsolódás az adatbázishoz</property>
        <property name="ShortLabel" translatable="yes">Kapcsolódás az adatbázishoz</property>
        <property name="StockId">gtk-connect</property>
      </action>
      <action id="SzmlkKezelseAction">
        <property name="Type">Action</property>
        <property name="Accelerator">&lt;Control&gt;&lt;Mod2&gt;o</property>
        <property name="Label" translatable="yes">_Számlák kezelése</property>
        <property name="ShortLabel" translatable="yes">Számlák kezelése...</property>
        <property name="StockId">gtk-dnd-multiple</property>
        <signal name="Activated" handler="OnSzmlkKezelseActivated" />
      </action>
      <action id="MrtkegysgekKezelseAction">
        <property name="Type">Action</property>
        <property name="Label" translatable="yes">_Mértékegységek kezelése</property>
        <property name="ShortLabel" translatable="yes">Mértékegységek kezelése</property>
        <property name="StockId">gtk-edit</property>
        <signal name="Activated" handler="OnMrtkegysgekKezelseActivated" />
      </action>
      <action id="TermkcsoportokKezelseAction">
        <property name="Type">Action</property>
        <property name="Label" translatable="yes">_Termékcsoportok kezelése</property>
        <property name="ShortLabel" translatable="yes">Termékcsoportok kezelése</property>
        <property name="StockId">gtk-edit</property>
        <signal name="Activated" handler="OnTermkcsoportokActivated" />
      </action>
    </action-group>
    <property name="MemberName" />
    <property name="Title" translatable="yes">Számlasegéd 1.0</property>
    <property name="WindowPosition">CenterAlways</property>
    <property name="Resizable">False</property>
    <property name="AllowGrow">False</property>
    <signal name="DeleteEvent" handler="OnDeleteEvent" />
    <signal name="FocusInEvent" handler="OnFocusInEvent" />
    <child>
      <widget class="Gtk.VBox" id="vbox1">
        <property name="MemberName" />
        <property name="Spacing">6</property>
        <child>
          <widget class="Gtk.MenuBar" id="menubar1">
            <property name="MemberName" />
            <node name="menubar1" type="Menubar">
              <node type="Menu" action="MveletekAction">
                <node type="Menuitem" action="jSzmlaKilltsaAction" />
                <node type="Menuitem" action="SzmlkKezelseAction" />
                <node type="Menuitem" action="gyfladatbzisMegnyitsaAction" />
                <node type="Menuitem" action="KszletadatbzisMegnyitsaAction" />
                <node type="Menuitem" action="AdatbzisMentseAction" />
                <node type="Menuitem" action="AdatbzisVisszalltsaAction" />
                <node type="Separator" />
                <node type="Menuitem" action="KilpsASzmlasegdblAction" />
              </node>
              <node type="Menu" action="BelltsokAction">
                <node type="Menuitem" action="Cginformcik" />
                <node type="Menuitem" action="MrtkegysgekKezelseAction" />
                <node type="Menuitem" action="TermkcsoportokKezelseAction" />
              </node>
              <node type="Menu" action="Sg">
                <node type="Menuitem" action="PrograminformcikAction" />
                <node type="Menuitem" action="FelhasznliDokumentciAction" />
              </node>
            </node>
          </widget>
          <packing>
            <property name="Position">0</property>
            <property name="AutoSize">True</property>
            <property name="Expand">False</property>
            <property name="Fill">False</property>
          </packing>
        </child>
        <child>
          <widget class="Gtk.Image" id="image111">
            <property name="MemberName" />
            <property name="Pixbuf">resource:bg.gif</property>
          </widget>
          <packing>
            <property name="Position">1</property>
            <property name="AutoSize">False</property>
            <property name="Fill">False</property>
          </packing>
        </child>
        <child>
          <widget class="Gtk.Statusbar" id="statusbar1">
            <property name="MemberName" />
            <property name="Spacing">6</property>
            <property name="BorderWidth">1</property>
            <child>
              <placeholder />
            </child>
            <child>
              <placeholder />
            </child>
          </widget>
          <packing>
            <property name="PackType">End</property>
            <property name="Position">2</property>
            <property name="AutoSize">True</property>
            <property name="Expand">False</property>
            <property name="Fill">False</property>
            <property name="Padding">2</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>

```

The window isn't too complicated, it has a vbox with 3 rows, the first one contains a menu, the second one an image and the last one holds a status bar. The strange thing is that it makes no difference which window I use, the same problem happens.

Is this a bug in my application or rather in the GTK libraries?

Stack trace:

```

Stacktrace:

  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0xffffffff>
  at Gtk.Application.Run () <0x00007>
  at Számlasegéd.Szamlaseged.Main (string[]) <0x0006f>
  at (wrapper runtime-invoke) Számlasegéd.Szamlaseged.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	mono [0x806d944]
	mono [0x808616b]
	[0xb7fc1410]
	/usr/lib/libX11.so.6 [0xb677221f]
	/usr/lib/libX11.so.6(XrmQGetResource+0x3e) [0xb6788dce]
	/usr/lib/libX11.so.6(XGetDefault+0xcb) [0xb676845b]
	/usr/lib/libcairo.so.2 [0xb66ee978]
	/usr/lib/libcairo.so.2 [0xb66eeca4]
	/usr/lib/libcairo.so.2 [0xb66ef5bc]
	/usr/lib/libcairo.so.2(cairo_xlib_surface_create+0x10a) [0xb66efd6a]
	/usr/lib/libgdk-x11-2.0.so.0 [0xb68dceb1]
	/usr/lib/libgdk-x11-2.0.so.0 [0xb68b0923]
	/usr/lib/libgdk-x11-2.0.so.0 [0xb68bcb60]
	/usr/lib/libgdk-x11-2.0.so.0 [0xb68b0923]
	/usr/lib/libgdk-x11-2.0.so.0(gdk_window_begin_paint_region+0x11e) [0xb68c99ee]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x51e) [0xb6a5555e]
	/usr/lib/libgdk-x11-2.0.so.0 [0xb68c9e95]
	/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0xff) [0xb68ca4af]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb69cc4cf]
	/usr/lib/libgdk-x11-2.0.so.0 [0xb68ad8fb]
	/usr/lib/libglib-2.0.so.0 [0xb7f26c81]
	/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8) [0xb7f28b88]
	/usr/lib/libglib-2.0.so.0 [0xb7f2c0eb]
	/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca) [0xb7f2c5ba]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9) [0xb6a557d9]
	[0xb5f9a85e]
	[0xb5f9a828]
	[0xb7843c18]
	[0xb78431b3]
	mono(mono_runtime_exec_main+0xe5) [0x80bad75]
	mono(mono_runtime_run_main+0x16b) [0x80bb4eb]
	mono(mono_main+0x1727) [0x805c917]
	mono [0x805ac62]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7d55775]
	mono [0x805aba1]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7d0b6e0 (LWP 19838)]
[New Thread 0xb744ab90 (LWP 19840)]
[New Thread 0xb746eb90 (LWP 19839)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7fc1430 in __kernel_vsyscall ()
  3 Thread 0xb746eb90 (LWP 19839)  0xb7fc1430 in __kernel_vsyscall ()
  2 Thread 0xb744ab90 (LWP 19840)  0xb7fc1430 in __kernel_vsyscall ()
  1 Thread 0xb7d0b6e0 (LWP 19838)  0xb7fc1430 in __kernel_vsyscall ()

Thread 3 (Thread 0xb746eb90 (LWP 19839)):
#0  0xb7fc1430 in __kernel_vsyscall ()
#1  0xb7ed58f6 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081492e8 in ?? ()
#3  0xb7ece4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7e2349e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb744ab90 (LWP 19840)):
#0  0xb7fc1430 in __kernel_vsyscall ()
#1  0xb7ed20e5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0814c607 in ?? ()
#3  0x0814f1f4 in ?? ()
#4  0x0814f25c in ?? ()
#5  0x08169b02 in ?? ()
#6  0x080d565a in ?? ()
#7  0x080f7639 in ?? ()
#8  0x081653b6 in ?? ()
#9  0x08183355 in ?? ()
#10 0xb7ece4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7e2349e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7d0b6e0 (LWP 19838)):
#0  0xb7fc1430 in __kernel_vsyscall ()
#1  0xb7e1fa87 in syscall () from /lib/tls/i686/cmov/libc.so.6
#2  0x0806d9e7 in ?? ()
#3  0x0808616b in ?? ()
#4  <signal handler called>
#5  0xb7ecf9e0 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#6  0xb677221f in ?? () from /usr/lib/libX11.so.6
#7  0xb6788dce in XrmQGetResource () from /usr/lib/libX11.so.6
#8  0xb676845b in XGetDefault () from /usr/lib/libX11.so.6
#9  0xb66ee978 in ?? () from /usr/lib/libcairo.so.2
#10 0xb66eeca4 in ?? () from /usr/lib/libcairo.so.2
#11 0xb66ef5bc in ?? () from /usr/lib/libcairo.so.2
#12 0xb66efd6a in cairo_xlib_surface_create () from /usr/lib/libcairo.so.2
#13 0xb68dceb1 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#14 0xb68b0923 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#15 0xb68bcb60 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#16 0xb68b0923 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#17 0xb68c99ee in gdk_window_begin_paint_region ()
   from /usr/lib/libgdk-x11-2.0.so.0
#18 0xb6a5555e in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#19 0xb68c9e95 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#20 0xb68ca4af in gdk_window_process_all_updates ()
   from /usr/lib/libgdk-x11-2.0.so.0
#21 0xb69cc4cf in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#22 0xb68ad8fb in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#23 0xb7f26c81 in ?? () from /usr/lib/libglib-2.0.so.0
#24 0xb7f28b88 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#25 0xb7f2c0eb in ?? () from /usr/lib/libglib-2.0.so.0
#26 0xb7f2c5ba in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#27 0xb6a557d9 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#28 0xb5f9a85e in ?? ()
#29 0xb5f9a828 in ?? ()
#30 0xb7843c18 in ?? ()
#31 0xb78431b3 in ?? ()
#32 0x080bad75 in mono_runtime_exec_main ()
#33 0x080bb4eb in mono_runtime_run_main ()
#34 0x0805c917 in mono_main ()
#35 0x0805ac62 in ?? ()
#36 0xb7d55775 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#37 0x0805aba1 in ?? ()
#0  0xb7fc1430 in __kernel_vsyscall ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

Thanks for your help!

---

### Post by directhex on 2009-11-11
I'd file an upstream bug on the Novell bugzilla.

---

### Post by kissg1988 on 2009-11-11
I've posted a bug report, now let's hope it will be fixed soon (in case it really is a bug)...

[https://bugzilla.novell.com/show_bug.cgi?id=554678]("https://bugzilla.novell.com/show_bug.cgi?id=554678")

---

### Post by kissg1988 on 2009-11-15
No response, yet. I'm going to try to report this to GTK developers, too.

[https://bugzilla.gnome.org/show_bug.cgi?id=602023](https://bugzilla.gnome.org/show_bug.cgi?id=602023)

---

### Post by kissg1988 on 2009-11-18
The problem has been solved! Removing the following lines from the source eliminated the issue:

```

// Felbontás ellen&#337;rzése
   System.Drawing.Size screensize = System.Windows.Forms.SystemInformation.PrimaryMonitorSize;
			if(screensize.Width<800)
				PopupDialog.ShowErrorMessage("Hiba","A Számlasegéd használatához legalább 800x600-as képerny&#337;felbontás szükséges. Állítsa be a felbontást a megfelel&#337; m&#369;ködés érdekében.");

```

In fact, it's a workaround rather than a solution, but it's completely acceptable for me. I wonder, though, why did this code cause an exception...

---

### Post by directhex on 2009-11-18
Possibly some conflict between the WinForms and GTK+ threading/drawing models? You can't mix them together.

---


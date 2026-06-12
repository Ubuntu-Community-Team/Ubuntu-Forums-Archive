---
title: "[VALA] Tray application"
date: 2010-08-24
forum: Programming Talk
---

### Post by arvigeus on 2010-08-24
Anyone here experienced with Vala? I found it recently and I think it looks promising. I'm taking my first steps into GUI programming and have no background experience with it. Can somebody post a snippet of a tray app with simple menu attached to it?

---

### Post by kahumba on 2010-08-24
Haven't tested it, just googled and found:
[http://code.valaide.org/content/genie-simple-statusicon-test](http://code.valaide.org/content/genie-simple-statusicon-test)

Also, the Vala docs with samples including GTK-related ones are at:
[http://live.gnome.org/Vala/Documentation](http://live.gnome.org/Vala/Documentation)

Ubuntu 10.04 comes with Vala 0.8 which I found slightly buggy and with Ubuntu 10.10 which comes with 0.9.7 I had no issues, so I decided to continue learning Vala after Ubuntu 10.10 gets released.

---

### Post by kahumba on 2010-08-24
Aaa.. forget it... that example seems crap.

---

### Post by arvigeus on 2010-08-26
I know that example, but it looks like pure python.
For now I'll settle for plain gtk C

---

### Post by arvigeus on 2010-08-29
I think this is the answer: [http://code.google.com/p/xnoise/source/browse/xnoise/src/xnoise-tray-icon.vala?r=b4e2d3387b813f1a67bd5118e54cd78810a448d2](http://code.google.com/p/xnoise/source/browse/xnoise/src/xnoise-tray-icon.vala?r=b4e2d3387b813f1a67bd5118e54cd78810a448d2)

But For some reason, when compiling it throws:
```
error: The type name `Main' could not be found
	private unowned Main xn;
	        ^^^^^^^^^^^^

```

---

### Post by kahumba on 2010-08-29
I think the Main class extends the Gtk Window class and the author didn't post its contents, so you ether have to create your own or modify that example to get along without having to reference it.

---

### Post by arvigeus on 2010-10-15
I almost solved this. The above example was actually in Genie (a Python-like dialect of Vala). I have only one problem: Can't make the menu to popup on left click. What could it be? Here is the code: (look at line 16)
```
using Gtk;
 
public class Main {

  class AppStatusIcon : Window {
    private StatusIcon trayicon;
    private Menu menuMain;
    private Menu menuSystem;

    public AppStatusIcon() {
      /* Create tray icon */
      trayicon = new StatusIcon.from_stock(STOCK_HOME);
      trayicon.set_tooltip_text ("Tray");
      trayicon.set_visible(true);
      /* Why is this not working? */
      /* trayicon.activate.connect(menuMain_popup); */
      create_menuMain();
      create_menuSystem();
    }

/* Create menu for left button */
    public void create_menuMain() {
      menuMain = new Menu();
      var menuAbout = new ImageMenuItem.from_stock(STOCK_ABOUT, null);
      menuAbout.activate.connect(about_clicked);
      menuMain.append(menuAbout);
      var menuQuit = new ImageMenuItem.from_stock(STOCK_QUIT, null);
      menuQuit.activate.connect(Gtk.main_quit);
      menuMain.append(menuQuit);
      menuMain.show_all();
    }

    /* Show popup menu on left button */
    private void menuMain_popup(uint button, uint time) {
      menuMain.popup(null, null, null, button, time);
    }

    /* Create menu for right button */
    public void create_menuSystem() {
      menuSystem = new Menu();
      var menuAbout = new ImageMenuItem.from_stock(STOCK_ABOUT, null);
      menuAbout.activate.connect(about_clicked);
      menuSystem.append(menuAbout);
      var menuQuit = new ImageMenuItem.from_stock(STOCK_QUIT, null);
      menuQuit.activate.connect(Gtk.main_quit);
      menuSystem.append(menuQuit);
      menuSystem.show_all();
      trayicon.popup_menu.connect(menuSystem_popup);
    }

    /* Show popup menu on right button */
    private void menuSystem_popup(uint button, uint time) {
      stdout.printf("%u, %u", button, time);
      menuSystem.popup(null, null, null, button, time);
    }

    private void about_clicked() {
      var about = new AboutDialog();
      about.set_version("0.0.0");
      about.set_program_name("Tray");
      about.set_comments("Tray utility");
      about.set_copyright("vala");
      about.run();
      about.hide();
    }
  }
  
  public static int main (string[] args) {
    Gtk.init(ref args);
    var App = new AppStatusIcon();
    App.hide();
    Gtk.main();
    return 0;
  }
}
```

---

### Post by anatolik on 2011-03-11
> **arvigeus said:**
> I almost solved this. The above example was actually in Genie (a Python-like dialect of Vala). I have only one problem: Can't make the menu to popup on left click. What could it be? Here is the code: (look at line 16)

Ok, here the working code:

```
using Gtk;
 
public class Main {

  class AppStatusIcon : Window {
    private StatusIcon trayicon;
    private Menu menuSystem;

    public AppStatusIcon() {
      /* Create tray icon */
      trayicon = new StatusIcon.from_stock(Stock.HOME);
      trayicon.set_tooltip_text ("Tray");
      trayicon.set_visible(true);

      trayicon.activate.connect(about_clicked);

      create_menuSystem();
      trayicon.popup_menu.connect(menuSystem_popup);
    }

    /* Create menu for right button */
    public void create_menuSystem() {
      menuSystem = new Menu();
      var menuAbout = new ImageMenuItem.from_stock(Stock.ABOUT, null);
      menuAbout.activate.connect(about_clicked);
      menuSystem.append(menuAbout);
      var menuQuit = new ImageMenuItem.from_stock(Stock.QUIT, null);
      menuQuit.activate.connect(Gtk.main_quit);
      menuSystem.append(menuQuit);
      menuSystem.show_all();
    }

    /* Show popup menu on right button */
    private void menuSystem_popup(uint button, uint time) {
      menuSystem.popup(null, null, null, button, time);
    }

    private void about_clicked() {
      var about = new AboutDialog();
      about.set_version("0.0.0");
      about.set_program_name("Tray");
      about.set_comments("Tray utility");
      about.set_copyright("vala");
      about.run();
      about.hide();
    }
  }
  
  public static int main (string[] args) {
    Gtk.init(ref args);
    var App = new AppStatusIcon();
    App.hide();
    Gtk.main();
    return 0;
  }
}
```

You cannot compile your application because SystemIcon.activate is a function with 0 arguments. See its API here: [http://valadoc.org/references/gtk+-2.0/0.11.5/Gtk.StatusIcon.activate.html](http://valadoc.org/references/gtk+-2.0/0.11.5/Gtk.StatusIcon.activate.html)

So you need to rewrite your method (I connected "about" popup to it).

---


---
title: "Gecko &amp; C#"
date: 2009-02-05
forum: Programming Talk
---

### Post by matmatmat on 2009-02-05
I've just started using mono & c#. I installed gecko (a tutorial I was following recommended installing it) & copied the browser code from the documentation & added a few features:
[PHP]
using System;
using Gtk;
using Gecko;
using System.IO;

namespace g_browser
{
	class GeckoTest
	{
		WebControl moz;
		Entry entry;
		string currentUrl;
		Statusbar sb;
		ProgressBar pb;
		
		static void Main (string[] args)
		{
			new GeckoTest ();
		}
		
		GeckoTest ()
		{
			Application.Init ();
			
			Window win = new Window ("Waterfox");
			win.SetDefaultSize (800, 600);
			win.DeleteEvent += new DeleteEventHandler (window_delete);
			
			VBox vbox = new VBox (false, 1);
			win.Add (vbox);
			
			HBox tb = new HBox (true, 1);
			Button btnBack = new Button (Gtk.Stock.GoBack);
			btnBack.Clicked += new EventHandler (on_btnBack_clicked);
			Button btnForward = new Button (Gtk.Stock.GoForward);
			btnForward.Clicked += new EventHandler (on_btnForward_clicked);
			Button btnStop = new Button (Gtk.Stock.Stop);
			btnStop.Clicked += new EventHandler (on_btnStop_clicked);
			Button btnRefresh = new Button (Gtk.Stock.Refresh);
			btnRefresh.Clicked += new EventHandler (on_btnRefresh_clicked);
			tb.Add (btnBack);
			tb.Add (btnForward);
			tb.Add (btnStop);
			tb.Add (btnRefresh);
			
			vbox.PackStart (tb, false, false, 1);
			
			HBox hbox = new HBox (false, 2);
			
			Label label = new Label ("Address:");
			
			entry = new Entry ("");
			entry.Activated += new EventHandler (entry_activated);
			
			Button button = new Button ("GO!");
			button.Clicked += new EventHandler (button_clicked);		
			
			hbox.PackStart (label, false, false, 1);
			hbox.PackStart (entry, true, true, 1);
			hbox.PackStart (button, false, false, 1);
			
			vbox.PackStart (hbox, false, false, 1);
			
			moz = new WebControl ("/tmp/csharp", "GeckoTest");
			moz.LinkMsg += new EventHandler(on_moz_linkmessage);
			moz.LocChange += new EventHandler(on_locChange);
			moz.Realized += new EventHandler(rel);
			
			vbox.PackStart(moz, true, true, 1);
			
			HBox hbox2 = new HBox (false, 1);
			vbox.PackStart (hbox2, false, false, 1);
			
			sb = new Statusbar ();
			sb.Push (1, "Welcome!");
			hbox2.Add (sb);
			
			pb = new ProgressBar ();
			pb.Orientation = ProgressBarOrientation.LeftToRight;
			hbox2.Add (pb);
			
			win.ShowAll ();
			
			Application.Run ();		
			
		}
		
		void rel (object obj, EventArgs arg)
		{		
			if (File.Exists("/home/matio/.waterfox/home.txt"))
			{
				string home = File.ReadAllText("/home/matio/.waterfox/home.txt");
				LoadHtml(home);
			}
			else
			{
				string home = "www.google.co.uk";
				LoadHtml(home);
			}				
			
		}
				
		
		void window_delete (object obj, EventArgs args)
		{
			Application.Quit();
		}
		
		void on_locChange (object obj, EventArgs args)
		{
			string location = moz.Location;
			entry.Text = location;
			
		}		
		
		void button_clicked (object obj, EventArgs args)
		{
			string url = entry.Text.Trim();
			
			if (url.StartsWith("gg")){
				string n_url = url.Replace("gg", "");
				url = "http://www.google.co.uk/search?hl=en&q=" + n_url + "&btnG=Google+Search&meta=";
				LoadHtml (url);
			}	
			
			else if (url.StartsWith("home")){
				string n_url = url.Replace("home ", "");
				if (!File.Exists("/home/matio/.waterfox/home.txt")){
					Directory.CreateDirectory("/home/matio/.waterfox/");
					File.Create("/home/matio/.waterfox/home.txt");
				}
				File.WriteAllText("/home/matio/.waterfox/home.txt", n_url);
				entry.Text = moz.Location;
			}	
			
			else if(url.StartsWith("ghome")){
				rel(obj, args);
			}
						
			else if(url.StartsWith("bbc")){
				LoadHtml ("www.bbc.co.uk");
			}
			
			else if(url.StartsWith("sport")){
				LoadHtml ("http://www.skysports.com/");
			}	
		
			else if(url.StartsWith("bradfordfc")){
				LoadHtml ("http://www.bradfordcityfc.co.uk/page/Home/");
			}
			
			else if(url.StartsWith("ubuntu")){
				LoadHtml ("http://www.ubuntu.com/");
			}			

			else if(url.StartsWith("lxf")){
				LoadHtml ("http://www.linuxformat.co.uk/");
			}	
						
			else if(url.StartsWith("pyprojects")){
				LoadHtml ("http://www.daniweb.com/forums/thread32007.html");
			}	
			
			else if(url.StartsWith("chomp set")){
				string n_url = url.Replace("chomp set ", "");
				n_url += "\n";
				File.AppendAllText("/home/matio/sitelist.txt", n_url);
				entry.Text = moz.Location;
			}		
			
			else if(url.StartsWith("tux radar")){
				LoadHtml ("http://www.tuxradar.com/");
			}
			
			else if(url.StartsWith("help")){
				LoadHtml ("file:///home/matio/.waterfox/help.html");
			}
			
			
			else{
				LoadHtml (url);
			}
		}
			
		
		void on_moz_linkmessage (object obj, EventArgs args)
		{
			sb.Pop (1);
			sb.Push (1, moz.LinkMessage);
			
		}
		
		void entry_activated (object obj, EventArgs args)
		{
			button_clicked (obj, args);
		}
		
		void LoadHtml (string URL)
		{
			moz.LoadUrl (URL);
		}
		
		void on_btnBack_clicked (object obj, EventArgs args)
		{
			moz.GoBack();
		}

		void on_btnStop_clicked (object obj, EventArgs args)
		{
			moz.StopLoad();
		}

		void on_btnForward_clicked (object obj, EventArgs args)
		{
			moz.GoForward();
		}

		void on_btnRefresh_clicked (object obj, EventArgs args)
		{
			moz.Reload(0);
		}
			
	}
}
[/PHP] 
(chomp is an rss I copied/enhanced/made from a tutorial)

Questions:
1) Can you make it so that when you click on a download link, it downloads it - can it be done (& how)? 
2) When you right click in firefox, it comes up with options like copy, paste etc - how could it be done here?
3) How would you create a new window?

Thanks

---

### Post by matmatmat on 2009-02-05
Is there nobody here her uses gecko or mono?

---

### Post by directhex on 2009-02-05
> **matmatmat said:**
> Is there nobody here her uses gecko or mono?

I don't think it's the right place to speak to people using Gecko#, really. Mono forums, mailing lists, or IRC are likely to yield better results

---

### Post by matmatmat on 2009-02-07
I posted it on the mono mailing list & apparently there is no way to do any of the above!
Does anyone know if gecko (not gecko-sharp) does the above?
Thanks

---

### Post by directhex on 2009-02-07
Perhaps webkit# will give better results?

---

### Post by matmatmat on 2009-02-07
I installed it, but how do you use it?

---

### Post by directhex on 2009-02-07
> **matmatmat said:**
> I installed it, but how do you use it?

There's a very simple demo browser in the source package

---

### Post by matmatmat on 2009-02-07
Well, I think I installed it, using:
```

sudo apt-get install libwebkit*

```

---

### Post by directhex on 2009-02-07
> **matmatmat said:**
> Well, I think I installed it, using:
```

sudo apt-get install libwebkit*

```

apt-get source webkit-sharp

---


---
title: "Window doesn't refresh after a while"
date: 2007-12-28
forum: Programming Talk
---

### Post by PeumansJoris on 2007-12-28
Hello forum
I'm a newby in Linux and Mono (and GTK)):P. I'm using Gutsy + Mono 1.2.6. Next program compiles and runs under mono, but has a very strange behaviour after a undefined amount of seconds (sometimes 3, sometimes 137 or 159 ...): when you minimise and maximise it again, all the widgets are disappeared. So the screens blanks out. Does someone have any suggestions ?
Thanks for your help.
Joris

Please note you have to change the filepath of the 2 "txt" files;


```

// project created on 10-12-2007 at 19:04
using System;
using System.IO;
using Gtk;
using Pango;
using System.Timers;
 
public class TruckPC
{
   private static System.Timers.Timer myTimer; 
   public static void Main() 
   {
     	Application.Init();
     
     	Toon oToon = new Toon();
    	IniData oIniData = new IniData();
          
     	IniData.LeesSettings("/home/joris/truckpc_settings.txt");
     	IniData.LeesData("/home/joris/truckpc_info.txt");
	
		Toon.InitialiseerScherm();
  		Toon.Initialiseer();
	    Toon.VerversData();
		
		myTimer = new System.Timers.Timer();
		myTimer.Elapsed += new ElapsedEventHandler(UpdateEvent);
		myTimer.Interval = 1000;
		myTimer.Enabled = true;
		
        Application.Run();   
    }
    
    public static void UpdateEvent(object source, ElapsedEventArgs e)
    {
	    IniData.LeesData("/home/joris/truckpc_info.txt");
		Toon.VerversData();	
	}
}

public class Toon
{
	static Table tb_small0 = new Table (5,5,false);
    static Label label0 = new Label("");
    static Label labelf0 = new Label("");
    static Label labelu0 = new Label("");
	static Table tb_small1 = new Table (5,5,false);
    static Label label1 = new Label("");
    static Label labelf1 = new Label("");
    static Label labelu1 = new Label("");
    static Table tb_small2 = new Table (5,5,false);
    static Label label2 = new Label("");
    static Label labelf2 = new Label("");
    static Label labelu2 = new Label("");
    static Table tb_small3 = new Table (5,5,false);
    static Label label3 = new Label("");
    static Label labelf3 = new Label("");
    static Label labelu3 = new Label("");
    static Table tb_small4 = new Table (5,5,false);
    static Label label4 = new Label("");
    static Label labelf4 = new Label("");
    static Label labelu4 = new Label("");
    static Table tb_small5 = new Table (5,5,false);
    static Label label5 = new Label("");
    static Label labelf5 = new Label("");
    static Label labelu5 = new Label("");
    static Table tb_large = new Table (6,6,false);
    static IniData oIniData = new IniData();
    static Window myWin = new Window("TruckPC");
    
    static bool EersteRun = true;
    
    static int teller = 0;
    
	public static void InitialiseerScherm()
	{
	    // Delete event
        myWin.DeleteEvent += delegate {Application.Quit ();};
        myWin.ShowAll();
    }

    public static void Initialiseer()
    {
     	myWin.Add(tb_large);
    }

	public static void VerversData()
	{
    	int i = 0;
		while (i <= 5)
	    {
		    int k = 0;
			while (oIniData.GetAfkorting(k) != oIniData.GetSchermBlok(i))
			{
				k++;
			}
			switch (i)
				{case 0:
					label0.Text = oIniData.GetOmschrijving(k);
					labelf0.Text = oIniData.GetWaarde(k);
					labelu0.Text = oIniData.GetEenheid(k);
					if (EersteRun)
					{
					    	label0.ModifyFont(FontDescription.FromString("FreeSans 12"));
						label0.SetAlignment(0,0);
						labelf0.ModifyFont(FontDescription.FromString("Bitwise 72"));
			            	    	labelf0.SetAlignment(1,0);
					    	labelu0.ModifyFont(FontDescription.FromString("FreeSans 22"));
						labelu0.SetAlignment(1,0);
						tb_small0.Attach(label0, 0,4,0,1);
						tb_small0.Attach(labelf0, 0,5,1,5);
						tb_small0.Attach(labelu0, 3,5,0,1);
					    	tb_large.Attach(tb_small0,0,1,0,1);
				    	}
					label0.Show();
					labelf0.Show();
					labelu0.Show();
					break;
/*				    case 1:
					label1.Text = oIniData.GetOmschrijving(k);
					labelf1.Text = oIniData.GetWaarde(k);
					labelu1.Text = oIniData.GetEenheid(k);
					if (EersteRun)
					{
					    label1.ModifyFont(FontDescription.FromString("FreeSans 12"));
						label1.SetAlignment(0,0);
						labelf1.ModifyFont(FontDescription.FromString("Bitwise 72"));
			            labelf1.SetAlignment(1,0);
					    labelu1.ModifyFont(FontDescription.FromString("FreeSans 22"));
						labelu1.SetAlignment(1,0);
						tb_small1.Attach(label1, 0,4,0,1);
						tb_small1.Attach(labelf1, 0,5,1,5);
						tb_small1.Attach(labelu1, 3,5,0,1);
					    tb_large.Attach(tb_small1,2,3,0,1);
				    }
				    break;
				    case 2:
					label2.Text = oIniData.GetOmschrijving(k);
					labelf2.Text = oIniData.GetWaarde(k);
					labelu2.Text = oIniData.GetEenheid(k);
					if (EersteRun)
					{
					    label2.ModifyFont(FontDescription.FromString("FreeSans 12"));
						label2.SetAlignment(0,0);
						labelf2.ModifyFont(FontDescription.FromString("Bitwise 72"));
			            labelf2.SetAlignment(1,0);
					    labelu2.ModifyFont(FontDescription.FromString("FreeSans 22"));
						labelu2.SetAlignment(1,0);
						tb_small2.Attach(label2, 0,4,0,1);
						tb_small2.Attach(labelf2, 0,5,1,5);
						tb_small2.Attach(labelu2, 3,5,0,1);
					    tb_large.Attach(tb_small2,4,5,0,1);
				    }
				    break;
				    case 3:
					label3.Text = oIniData.GetOmschrijving(k);
					labelf3.Text = oIniData.GetWaarde(k);
					labelu3.Text = oIniData.GetEenheid(k);
					if (EersteRun)
					{
					    label3.ModifyFont(FontDescription.FromString("FreeSans 12"));
						label3.SetAlignment(0,0);
						labelf3.ModifyFont(FontDescription.FromString("Bitwise 72"));
			            labelf3.SetAlignment(1,0);
					    labelu3.ModifyFont(FontDescription.FromString("FreeSans 22"));
						labelu3.SetAlignment(1,0);
						tb_small3.Attach(label3, 0,4,0,1);
						tb_small3.Attach(labelf3, 0,5,1,5);
						tb_small3.Attach(labelu3, 3,5,0,1);
					    tb_large.Attach(tb_small3,0,1,2,3);
				    }
				    break;
				    case 4:
					label4.Text = oIniData.GetOmschrijving(k);
					labelf4.Text = oIniData.GetWaarde(k);
					labelu4.Text = oIniData.GetEenheid(k);
					if (EersteRun)
					{
					    label4.ModifyFont(FontDescription.FromString("FreeSans 12"));
						label4.SetAlignment(0,0);
						labelf4.ModifyFont(FontDescription.FromString("Bitwise 72"));
			            labelf4.SetAlignment(1,0);
					    labelu4.ModifyFont(FontDescription.FromString("FreeSans 22"));
						labelu4.SetAlignment(1,0);
						tb_small4.Attach(label4, 0,4,0,1);
						tb_small4.Attach(labelf4, 0,5,1,5);
						tb_small4.Attach(labelu4, 3,5,0,1);
					    tb_large.Attach(tb_small4,2,3,2,3);
				    }
				    break;
				    case 5:
					label5.Text = oIniData.GetOmschrijving(k);
					labelf5.Text = oIniData.GetWaarde(k);
					labelu5.Text = oIniData.GetEenheid(k);
					if (EersteRun)
					{
					    label5.ModifyFont(FontDescription.FromString("FreeSans 12"));
						label5.SetAlignment(0,0);
						labelf5.ModifyFont(FontDescription.FromString("Bitwise 72"));
			            labelf5.SetAlignment(1,0);
					    labelu5.ModifyFont(FontDescription.FromString("FreeSans 22"));
						labelu5.SetAlignment(1,0);
						tb_small5.Attach(label5, 0,4,0,1);
						tb_small5.Attach(labelf5, 0,5,1,5);
						tb_small5.Attach(labelu5, 3,5,0,1);
					    tb_large.Attach(tb_small5,4,5,2,3);
				    }
				    break;*/
				    default:
				    break;
				 }
			i++;

		}
		if (EersteRun)
		{
			EersteRun = false;
		}
		myWin.Title = "TruckPC - " + teller++;
		myWin.ShowAll();
	}
}

public class IniData
{
   private static string[] Afkorting = new string[10];
   private static string[] Omschrijving  = new string[10];
   private static string[] Waarde = new string[10];
   private static string[] Eenheid = new string[10];
   private static string[] SchermBlok = new string[6];

	public string GetAfkorting(int i)
	{
		return Afkorting[i];
	}
	public string GetOmschrijving(int i)
	{
		return Omschrijving[i];
	}
	public string GetWaarde(int i)
	{
		return Waarde[i];
	}
	public string GetEenheid(int i)
	{
		return Eenheid[i];
	}
	public string GetSchermBlok(int i)
	{
		return SchermBlok[i];
	}

   public static void LeesData(string BestandNaam)
   {
// 			if (File.Exists(BestandNaam)) { Console.WriteLine (BestandNaam +" bestaat");}
		
		    FileStream fs = new FileStream(BestandNaam, FileMode.OpenOrCreate, FileAccess.Read);

   	     	StreamReader r = new StreamReader(fs);        
      		r.BaseStream.Seek(0, SeekOrigin.Begin);
      		int i = 0;
      		string s;
      		while (r.Peek() > -1)
      		{ // While not at the end of the file, write to standard output.
      			s = r.ReadLine();
				Afkorting[i] = s.Substring(0, 3);
				Omschrijving[i] = s.Substring(4, 25);
				Waarde[i] = s.Substring(29, 5);
				Eenheid[i] = s.Substring(35);
        		i++;
      		}
      		r.Close();
    }
    
   public static void LeesSettings(string BestandNaam)
   {
//			if (File.Exists(BestandNaam)) { Console.WriteLine (BestandNaam + " bestaat");}
		
		    FileStream fs = new FileStream(BestandNaam, FileMode.OpenOrCreate, FileAccess.Read);

   	     	StreamReader r = new StreamReader(fs);        
      		r.BaseStream.Seek(0, SeekOrigin.Begin);

      		string s;
      		while (r.Peek() > -1)
      		{ // While not at the end of the file, write to standard output.
      			s = r.ReadLine();
      			if (s == "_screensettings")
      				{
						s = r.ReadLine();
						SchermBlok[0] = s.Substring(0,3);
						SchermBlok[1] = s.Substring(4,3);						
  						SchermBlok[2] = s.Substring(8,3);    				
  						SchermBlok[3] = s.Substring(12,3);    			
  						SchermBlok[4] = s.Substring(16,3);
  					    SchermBlok[5] = s.Substring(20,3);
  					 }
      		}
      		r.Close();
    }
}

```

**truckpc_settings.txt:**
```

_screensettings
WTE,OPE,OTE,WL ,WTC,OTS
```

[B]
truckpc_info.txt:[/B]
```

OPE OilPressureEngine          3.5 bar
WL  WaterLevel                  OK    
OTE OilTemperatureEngine      92.0 °C 
WTE WaterTemperatureEngine   102.5 °C 
WTC WaterTemperatureCooler    50.0 °C 
OTH OilTemperatureHydraulics  65.0 °C 
OTG OilTemperatureGearbox     72.5 °C 
APT AirPressureTurbo           1.2 bar
OTS OilTemperatureShocks      67.0 °C

```

---

### Post by PeumansJoris on 2007-12-30
OK, nobody ? I'll give it a try in Python in that case ... and keep you posted.
Regards
Joris

---


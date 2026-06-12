---
title: "How messy is my code?"
date: 2009-10-10
forum: Programming Talk
---

### Post by matmatmat on 2009-10-10
How should I make it less messy?
```

using System;
using Gtk;
using Mono.Data.Sqlite;
using System.IO;

public partial class MainWindow: Gtk.Window
{	
	//SQLite variables
	static SqliteConnection DataConn;
    static SqliteCommand DataComm = new SqliteCommand();
    static SqliteDataReader DataReader;	
	string dsn;
	
	//tree_1 variables
	Gtk.TreeViewColumn name_1 = new Gtk.TreeViewColumn ();
	Gtk.ListStore List_1 = new Gtk.ListStore (typeof (string));
	Gtk.CellRendererText NameCell_1 = new Gtk.CellRendererText ();
	
	//tree_2 variables
	Gtk.TreeViewColumn home_team_2 = new Gtk.TreeViewColumn ();
	Gtk.TreeViewColumn away_team_2 = new Gtk.TreeViewColumn ();
	Gtk.TreeStore List_2 = new Gtk.TreeStore (typeof (string), typeof (string));
	Gtk.CellRendererText homeCell_2 = new Gtk.CellRendererText ();	
	Gtk.CellRendererText awayCell_2 = new Gtk.CellRendererText ();
	
	//Any
	Gtk.TreeIter iter;
	
	int numofteams;
	string[] teamsa;
	string[] homea;
	string[] awaya;
	int[,] fixturea;
	
	public void generate_fixtures()
	{
		Random rand = new Random();
		int home;
		int away;
		int numoffix = numofteams/2;
		int j = 0;
		homea = new string[numoffix + 2];
		awaya = new string[numoffix + 2];
		int[] teamsused = new int[numofteams];
		for (int i = 0; i < numoffix; i++){
			do{
				home = rand.Next(0, numofteams);
				away = rand.Next(0, numofteams);
			} while (home == away || fixturea[home,away] != 0 || teamsused[home] != 0 || teamsused[away] != 0);
			fixturea[home,away] = 1;
			homea[j] = teamsa[home];
			awaya[j] = teamsa[away];
			teamsused[home] = 1;
			teamsused[away] = 1;
			j++;
		}
	}
	
	public void generate_all_fixtures()
	{
		fixturea = new int[numofteams,numofteams];
		DataComm.CommandText = "DELETE FROM fixture;";
		DataComm.ExecuteNonQuery();	
		for (int i = 0; i <= (numofteams-2) * 2; i++){
			generate_fixtures();
			for (int j = 0; j < numofteams/2; j++){
				Console.WriteLine("{0} vs {1}", homea[j], awaya[j]);
				DataComm.CommandText = string.Format("INSERT INTO fixture VALUES (null, \"{0}\", \"{1}\", {2});", homea[j], awaya[j], i+1);
				DataComm.ExecuteNonQuery();				
			}
		}
		tree_2_add_data();
	}	
	
	public void generate_team_array()
	{
		DataComm.CommandText = "SELECT * FROM teams;";
		DataReader = DataComm.ExecuteReader();
		teamsa = new string[numofteams];
		int i = 0;
		string returned;
		while (DataReader.Read()){
			returned = DataReader["Name"].ToString();
			teamsa[i] = returned;
			i++;
		}	
		DataReader.Close();
	}
	
	public void tree_1_add_data()
	{
		numofteams = 0;
		DataComm.CommandText = "SELECT * FROM teams;";
		DataReader = DataComm.ExecuteReader();
		string returned;
		while (DataReader.Read()){
			returned = DataReader["Name"].ToString();
			List_1.AppendValues(returned);
			numofteams += 1;
		}
		DataReader.Close();
		generate_team_array();
	}
	
	public void tree_2_add_data()
	{
		string day;
		List_2.Clear();
		for (int i = 0; i < numofteams/2; i++){
			DataComm.CommandText = string.Format("SELECT * FROM fixture where Day = {0};", i+1);
			DataReader = DataComm.ExecuteReader();
			if (DataReader.HasRows){
				day = string.Format("Day {0}", i+1);
				iter = List_2.AppendValues(day);
			}
			while (DataReader.Read()){
				List_2.AppendValues(iter, DataReader["Home"].ToString(), DataReader["Away"].ToString());
				numofteams += 1;
			}
			DataReader.Close();	
			Console.WriteLine();
		}
	}
	
	public void tree_conf()
	{
		//tree_1
		name_1.Title = "Name"; 
		tree_1.AppendColumn(name_1);
		tree_1.Model = List_1;
		name_1.PackStart (NameCell_1, true);
		name_1.AddAttribute (NameCell_1, "text", 0);
		tree_1_add_data();
		
		//tree_2
		home_team_2.Title = "Home Team";
		away_team_2.Title = "Away Team";
		tree_2.AppendColumn(home_team_2);
		tree_2.AppendColumn(away_team_2);
		tree_2.Model = List_2;
		home_team_2.PackStart(homeCell_2, true);
		home_team_2.AddAttribute(homeCell_2, "text", 0);
		away_team_2.PackStart(awayCell_2, true);
		away_team_2.AddAttribute(awayCell_2, "text", 1);
		tree_2_add_data();
	}	
	
	public MainWindow (): base (Gtk.WindowType.Toplevel)
	{
		Build ();
		bool first = false;
		if (!File.Exists("league.db")){
			SqliteConnection.CreateFile("league.db");
			first = true;
		}
		string dsn = "Data Source=league.db;";
		DataConn = new SqliteConnection(dsn);
		DataConn.Open();
		DataComm.Connection = DataConn;
		if (first){
			DataComm.CommandText = "CREATE TABLE teams (ID INTEGER PRIMARY KEY, Name TEXT);";
			DataComm.ExecuteNonQuery();	
			DataComm.CommandText = "CREATE TABLE fixture (ID INTEGER PRIMARY KEY, Home TEXT, Away TEXT, Day INTEGER);";
			DataComm.ExecuteNonQuery();				
		}
		tree_conf();
	}
	
	protected void OnDeleteEvent (object sender, DeleteEventArgs a)
	{
		Application.Quit ();
		a.RetVal = true;
	}

	protected virtual void on_submit_1 (object sender, System.EventArgs e)
	{
		//if it's empty don't do anything
		string team = team_1.Text;
		if (team == ""){
			return;
		}
		//Insert data into the table
		DataComm.CommandText = string.Format("INSERT INTO teams VALUES (null, \"{0}\");", team);
		DataComm.ExecuteNonQuery();
		//Clear tree_1
		List_1.Clear();
		//Query database for teams
		tree_1_add_data();
	}

	protected virtual void on_generate_2 (object sender, System.EventArgs e)
	{
		generate_all_fixtures();
	}
}

```

---

### Post by MadCow108 on 2009-10-10
you should split implementation and gui.
writing one huge class to handle everything defeats the purpose of object orientation.

edit ignore following,  confused the language xD:
[i]you have no constructor and destructor, which are needed because are tons of memory leaks (every new must be matched with a delete, (or better use RAII, gtk provides the means for that))

I have never seen this before:
fixturea = new int[numofteams,numofteams];
what does that syntax do?[/i]

---

### Post by GuyCorngood on 2009-10-10
Yeah, it's pretty messy. I see three big areas you could work on before tackling the little things.

[LIST=1]
[*]You put all your code into one big class. It's hard at first to get a feel for designing classes, but it helps to remember the "object" part of object-oriented programming. "Is this a distinct 'thing'? Then it should be a new class!"
[*]You hard-coded your GUI layout. This is generally considered a bad idea: verbose, annoying to write, hard to maintain. It's fine for hello-world type programs when you're still learning the concepts behind GUI programming (or a few other special cases), but your program is a bit over that line. Instead, use Glade and GtkBuilder.
[*]You combined GUI code and business logic. Read up on the [model-view-controller]("http://en.wikipedia.org/wiki/Model–view–controller") pattern; it's how most well-designed GUI apps are built. Your program might be small enough for a combined model and controller, but it's almost never a good idea to combine model and view.
[/LIST]

---

### Post by GuyCorngood on 2009-10-10
> **MadCow108 said:**
> you have no constructor and destructor, which are needed because are tons of memory leaks (every new must be matched with a delete, (or better use RAII, gtk provides the means for that))

This is C#, so it's garbage-collected.

---

### Post by MadCow108 on 2009-10-10
woops it looks so similar to c++ :)
that explains the few points which confused me
sorry

---

### Post by matmatmat on 2009-10-10
> 
You hard-coded your GUI layout. This is generally considered a bad idea: verbose, annoying to write, hard to maintain. It's fine for hello-world type programs when you're still learning the concepts behind GUI programming (or a few other special cases), but your program is a bit over that line. Instead, use Glade and GtkBuilder.

I'm using Stetic

---

### Post by GuyCorngood on 2009-10-10
> **matmatmat said:**
> I'm using Stetic

Oh, that's good to hear. Come to think of it, the numbered variables should have clued me in. :rolleyes:

Actually, there's another bit of advice right there: use the GUI editor to name your controls. Code referring to "tree_2" is unclear compared to, say, "teams_tree".

> **MadCow108 said:**
> woops it looks so similar to c++ :)
that explains the few points which confused me
sorry

I thought it was too, at first. It looks like a lot of professionally-written C++ code I've seen. :P

---

### Post by cszikszoy on 2009-10-10
Why are you using primitive data types?  System.Collections.Generic is your friend.

I believe most (and in this case, all of the ones you are using) sqlite objects inherit from IDisposable, and *need* to be disposed, not just closed.  Using a "using" block can help you out with this by implicitly calling .Dispose() (which also calls .Close())

Here's an example:
```

using (SqliteCommand command = new SqliteCommand ()) {
    /*
    code.. code.. code..            
    */
}

```

---


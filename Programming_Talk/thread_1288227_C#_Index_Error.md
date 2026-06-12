---
title: "C# Index Error"
date: 2009-10-11
forum: Programming Talk
---

### Post by matmatmat on 2009-10-11
I have this code:
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
	
	//tree_3 variables
	Gtk.TreeViewColumn home_team_3 = new Gtk.TreeViewColumn ();
	Gtk.TreeViewColumn away_team_3 = new Gtk.TreeViewColumn ();
	Gtk.TreeViewColumn home_team_score_3 = new Gtk.TreeViewColumn ();
	Gtk.TreeViewColumn away_team_score_3 = new Gtk.TreeViewColumn ();	
	Gtk.TreeStore List_3 = new Gtk.TreeStore (typeof (string), typeof (string), typeof (string), typeof (string));
	Gtk.CellRendererText homeCell_3 = new Gtk.CellRendererText ();	
	Gtk.CellRendererText awayCell_3 = new Gtk.CellRendererText ();
	Gtk.CellRendererText homescoreCell_3 = new Gtk.CellRendererText ();
	Gtk.CellRendererText awayscoreCell_3 = new Gtk.CellRendererText ();
	
	//Iter
	Gtk.TreeIter iter_2;
	Gtk.TreeIter iter_3;
	
	int numofteams;
	int numofteamsOLD;
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
		homea = new string[numoffix];
		awaya = new string[numoffix];
		int[] teamsused = new int[numofteams];
		int k = 0;
		for (int i = 0; i < numoffix; i++){
			do{
				home = rand.Next(0, numofteams);
				away = rand.Next(0, numofteams);
				k++;
			} while (home == away || fixturea[home,away] != 0 || teamsused[home] != 0 || teamsused[away] != 0);
			fixturea[home,away] = 1;
      		//System.Diagnostics.Debug.Assert(i == j && j < numoffix && numoffix == homea.Length);
			Console.WriteLine(numofteams);
      		//homea[j] = "";
      		homea[j] = teamsa[home];	
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
		int blah = (numofteams-1) * 2;
		for (int i = 0; i < blah; i++){
			generate_fixtures();
			for (int j = 0; j < numofteams/2; j++){
				DataComm.CommandText = string.Format("INSERT INTO fixture VALUES (null, \"{0}\", \"{1}\", {2});", homea[j], awaya[j], i+1);
				DataComm.ExecuteNonQuery();	
				DataComm.CommandText = string.Format("INSERT INTO results VALUES (null, \"{0}\", null, \"{1}\", null, {2});", homea[j], awaya[j], i+1);
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
				iter_2 = List_2.AppendValues(day);
			} else {
				DataReader.Close();
				return;
			}
			while (DataReader.Read()){
				List_2.AppendValues(iter_2, DataReader["Home"].ToString(), DataReader["Away"].ToString());
				numofteams += 1;
			}
			DataReader.Close();	
		}
	}
	
	public void tree_3_add_data(){
		string day;
		List_3.Clear();
		for (int i = 0; i < numofteams/2; i++){
			DataComm.CommandText = string.Format("SELECT * FROM results where Day = {0};", i+1);
			DataReader = DataComm.ExecuteReader();
			if (DataReader.HasRows){
				day = string.Format("Day {0}", i+1);
				iter_3 = List_3.AppendValues(day);
			} else {
				DataReader.Close();
				return;
			}
			while (DataReader.Read()){
				List_3.AppendValues(iter_3, DataReader["Home"].ToString(), DataReader["Home_Score"].ToString(), DataReader["Away"].ToString(), DataReader["Away_Score"].ToString());
				numofteams += 1;
			}
			DataReader.Close();	
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
		
		//tree_3
		home_team_3.Title = "Home Team";
		away_team_3.Title = "Away Team";
		home_team_score_3.Title = "Home Score";
		away_team_score_3.Title = "Away Score";
		tree_3.AppendColumn(home_team_3);
		tree_3.AppendColumn(home_team_score_3);
		tree_3.AppendColumn(away_team_3);
		tree_3.AppendColumn(away_team_score_3);
		tree_3.Model = List_3;
		home_team_3.PackStart(homeCell_3, true);
		home_team_3.AddAttribute(homeCell_3, "text", 0);
		home_team_score_3.PackStart(homescoreCell_3, true);
		home_team_score_3.AddAttribute(homescoreCell_3, "text", 1);		
		away_team_3.PackStart(awayCell_3, true);
		away_team_3.AddAttribute(awayCell_3, "text", 2);
		away_team_score_3.PackStart(awayscoreCell_3, true);
		away_team_score_3.AddAttribute(awayscoreCell_3, "text", 3);		
		tree_3_add_data();
		Console.WriteLine(tree_3.Selection);
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
			DataComm.CommandText = "CREATE TABLE results (ID INTEGER PRIMARY KEY, Home TEXT, Home_Score INTEGER, Away TEXT, Away_Score INTEGER, Day INTEGER);";
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

	protected virtual void on_submit_3 (object sender, System.EventArgs e)
	{
	}
}

```
when you click on generate all fixtures (generate_2) it gives an "IndexOutOfRangeException" @ 69.

---

### Post by matmatmat on 2009-10-12
bump

---


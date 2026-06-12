---
title: "Mono, C#, SQLite Error"
date: 2009-10-08
forum: Programming Talk
---

### Post by matmatmat on 2009-10-08
I have this code:
```

using System;
using Gtk;
using Mono.Data.Sqlite;
using System.IO;

public partial class MainWindow: Gtk.Window
{	
	static SqliteConnection DataConn;
    static SqliteCommand DataComm = new SqliteCommand();
    static SqliteDataReader DataReader;	
	string dsn;
	
	Gtk.TreeViewColumn name = new Gtk.TreeViewColumn ();
	Gtk.ListStore List = new Gtk.ListStore (typeof (string));
	Gtk.CellRendererText NameCell = new Gtk.CellRendererText ();
	
	public void tree_add_data()
	{
		DataComm.CommandText = "SELECT * FROM teams;";
		DataReader = DataComm.ExecuteReader();
		string returned;
		while (DataReader.Read()){
			returned = DataReader["Name"].ToString();
			List.AppendValues(returned);
		}
	}	
	
	public void tree_conf()
	{
		name.Title = "Name"; 
		tree_1.AppendColumn(name);
		tree_1.Model = List;
		// Add the cell to the column
		name.PackStart (NameCell, true);
		name.AddAttribute (NameCell, "text", 0);
		tree_add_data();
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
		string team = team_1.Text;
		if (team == ""){
			return;
		}
		DataComm.CommandText = string.Format("INSERT INTO teams VALUES (null, \"{0}\");", team);
		DataComm.ExecuteNonQuery();
		List.Clear();
		tree_add_data();
	}
}

```
when you enter data into the entry & press submit it gives this error:
```

Marshaling clicked signal
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.InvalidOperationException: Cannot set CommandText while a DataReader is active
  at Mono.Data.Sqlite.SqliteCommand.set_CommandText (System.String value) [0x00000] 
  at MainWindow.on_submit_1 (System.Object sender, System.EventArgs e) [0x0001d] in /home/matio/Projects/leaguemanager/leaguemanager/MainWindow.cs:70 
  at (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] 
  at System.Delegate.DynamicInvokeImpl (System.Object[] args) [0x00000] 
  at System.MulticastDelegate.DynamicInvokeImpl (System.Object[] args) [0x00000] 
  at System.Delegate.DynamicInvoke (System.Object[] args) [0x00000] 
  at GLib.Signal.ClosureInvokedCB (System.Object o, GLib.ClosureInvokedArgs args) [0x00000] 
  at GLib.SignalClosure.Invoke (GLib.ClosureInvokedArgs args) [0x00000] 
  at GLib.SignalClosure.MarshalCallback (IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at leaguemanager.MainClass.Main(System.String[] args) in /home/matio/Projects/leaguemanager/leaguemanager/Main.cs:line 13

```
Do I have to wait for it to insert the data?

---

### Post by directhex on 2009-10-08
Your code can't compile as it's missing the GUI-related files. I can't test-compile it to bugfix it.

---

### Post by matmatmat on 2009-10-08
Attached...

---

### Post by directhex on 2009-10-08
Missing DataReader.Close() at the end of the tree_1_add_data() method.

---

### Post by matmatmat on 2009-10-08
Thanks, in C# can you do something like this:
```

int foo = 10;
int fooarray[foo][foo];

```

---

### Post by directhex on 2009-10-08
Don't see why not - why assign static arrays rather than using generics or arraylist, though? no need to worry about size then

---


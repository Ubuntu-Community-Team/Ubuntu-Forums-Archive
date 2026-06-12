---
title: "How to avoid running same tcl file twice ?"
date: 2009-04-06
forum: Programming Talk
---

### Post by tusharv on 2009-04-06
Hi All,

I have made one gui TK file.
Now how can I make sure that user should not able to run it more than one time simultaneously.

Means If it is already running and when user wants to run it second time then he should get the error.

One option is to make some lock file and check if it does exists or not. 
Is there any other option TK provides like [winfo exist .p2] for any top level existence ? I don't think this will work for the main window means 
[winfo exists .]

Thanks,
Tusharv

---

### Post by stevescripts on 2009-04-06
> **tusharv said:**
> 
...
One option is to make some lock file and check if it does exists or not. 

Is there any other option TK provides like [winfo exist .p2] for any top level existence ? I don't think this will work for the main window means 
[winfo exists .]


Indeed, creating a lock file of some sort is probably the easiest solution here, something like this:
```



proc app_running {fn} {
	if {[file exists $fn]} {
		message
	} else {
	
	set fn ./lockfile
	set fid [open $fn w+]
	puts -nonewline $fid "0"
	close $fid
	puts "Lockfile written"
	}
}

proc message { } {
	set result [tk_messageBox -type ok -message "Application is already running!"]
	if {[string eq $result "ok"]} {
	exit
	}
}

```

As multiple instances of tcl/tk running would allow multiple toplevels with the same names, [winfo exists ] won't get the job done here.

Hope this helps a bit.

Steve
(PS, it is up to your app to delete the lockfile on a clean exit...)

---

### Post by tusharv on 2009-04-07
Hi stevescripts,

Seriously I don't get what is "fn" passed to the procedure app_running and what is need to pass it.

Thanks,
Tushar

---

### Post by stevescripts on 2009-04-07
Tushar,

My bad there, I should have made the script a bit more specific -
fn for filename ...

Steve

---


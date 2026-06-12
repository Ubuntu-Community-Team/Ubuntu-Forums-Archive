---
title: "ikvm/java + resources + monodevelop = doesn't work?`"
date: 2009-03-10
forum: Programming Talk
---

### Post by zizzdude on 2009-03-10
Hey, I tried developing glade applications with monodevelop and java. I added gui.glade to the Resources folder, and used this code:

```

import cli.Gtk.*;
import cli.Glade.*;

public class MainClass
{
    public static void main(String[] args) 
    {
    	new MainClass();
    }
    
    public MainClass()
    {
    	Application.Init();
    	
    	XML gxml = new XML(null,"gui.glade", "window1", null);
    	gxml.Autoconnect(this);
    	
    	Application.Run();
    }  
}

```

The compilation was fine, but I get this error during runtime:

```

Exception in thread "main" cli.System.ArgumentException: Cannot get resource file 'gui.glade'
Parameter name: resource_name
	at cli.Glade.XML.<init>(Unknown Source)
	at MainClass.<init>(MainClass.java:20)
	at MainClass.main(MainClass.java:13)
	at <Module>.main(<Module>.java)
	at <Module>.main(<Module>.java)

```
Was there something I was missing?
Thanks

---


---
title: "Problems with java system calls that use redirects"
date: 2008-11-23
forum: Programming Talk
---

### Post by the_real_fourthdimension on 2008-11-23
Hey All

I'm programming a java app to start firefox, run a macro, and then kill firefox.  I am using this technique for the system calls:
```

Runtime.getRuntime().exec("my command");

```
That has worked well in the past.  However, now I want the runtime to run this command:
```

pidof firefox > pid

```
so that I can read in the pid with the scanner class and then kill it with the next command.  In debugging my program, I noticed that the redirect simply does not work when used by runtime.  Does anyone know how to get around this with either with a more efficient command or a different way of calling it?
Thanks a lot.

---

### Post by cl333r on 2008-11-23
If I understand you correctly you just need to read in the PID, if so try this:

```

try {
	Process p = Runtime.getRuntime().exec( "pidof firefox" );
	InputStream in = p.getInputStream();
	byte[] bytes = new byte[1024];
	//since expecting a very short string not using a loop
	int iReadCount = in.read( bytes );
	String str = new String( bytes, 0, iReadCount );
	System.out.println( "The pid is: " + str );

} catch( Exception exc ) {
	exc.printStackTrace();
}

```

---

### Post by geirha on 2008-11-23
Slightly easier/prettier if you wrap a Scanner around the inputStream
```

        Process p= Runtime.getRuntime().exec("pidof firefox");
        int retval= p.waitFor();
        if (retval != 0 ) throw new Exception("Firefox not running");
        Scanner s= new Scanner(p.getInputStream());
        while (s.hasNextInt())
            System.out.println("Firefox pid: "+s.nextInt());

```

---

### Post by the_real_fourthdimension on 2008-11-24
Thanks to both of you!
Am I correctly understanding that redirects cannot be used in system calls, then?

---

### Post by geirha on 2008-11-24
Using > as redirection is something the shell interprets. When you run something with Runtime.exec, you run it without a shell. If you want the > interpreted, you have to run it in a shell. E.g.:
```

String[] cmd= { "/bin/sh", "-c", "pidof firefox > /tmp/firefox.pid" };
Process p= Runtime.getRuntime().exec(cmd);

```

I recommend you rather do the redirection yourself in java by reading the InputStream, and writing it to a file or storing it in an object etc.

---


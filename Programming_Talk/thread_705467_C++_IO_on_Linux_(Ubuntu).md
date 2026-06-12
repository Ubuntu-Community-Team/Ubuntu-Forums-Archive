---
title: "C++ I/O on Linux (Ubuntu)"
date: 2008-02-23
forum: Programming Talk
---

### Post by xlinuks on 2008-02-23
Hi, I'm learning C++, moving from Java.
I wonder what libraries do C++ developers use on Ubuntu when developing apps? Are they using POSIX libraries or using some kind of wrappers through Glib (or something else)?
I got to the point where I can display widgets/dialogs (through Gtkmm) and now I wanna learn using Files. Any link or hint would be appreciated..

---

### Post by LaRoza on 2008-02-23
Look at my wiki for learning C++.

(Specifically, look into iostream and fstream)

---

### Post by xlinuks on 2008-02-23
Thanks...
I found
[http://www.gnu.org/software/libc/manual/html_node/File-System-Interface.html](http://www.gnu.org/software/libc/manual/html_node/File-System-Interface.html)
For instance, it turns out that finding out the current dir is as easy as
```

ustring sCurrentDir = getcwd( 0, 0 );

```
So far "Glib" seems to be easier than Java! Cool!

---

### Post by Shin_Gouki2501 on 2008-02-23
never had problems with Javas Filestream  and getPath() or getAbsolutePath()...

---

### Post by xlinuks on 2008-02-23
getPath & getAbsolutePath just get the path of _a_ dir, while I was talking about the current dir.
The System.getProperty( "user.dir" ) doesn't always work as one might wish.
When your app is a jar you actually have troubles determining the current dir, I found the solution to this issue not so long ago, which is pretty weird, you even have to take care of the OS and the file encoding, the only robust hand-coded implementation I did is this:
```

		URL url = thisClass.getProtectionDomain().getCodeSource().getLocation();
			boolean isWindows = System.getProperty( "os.name" ).toLowerCase().indexOf( "windows" ) > -1;
			try {
				String sPath = url.getPath();
				if( isWindows ) {
					sPath = URLDecoder.decode( sPath, "UTF8" );
				} else {
					sPath = URLDecoder.decode( sPath, System.getProperty( "file.encoding" ) );
				}
				File f = new File( sPath );
				if( !f.exists() ) {
					Log.tell( "file doesn't exist: " + f.getPath() );
					return null;
				}
				
				if( !f.isDirectory() ) { //then it's the .jar file and we need to get it's parent file
					parentDir = f.getParentFile();
				} else {
					parentDir = f;
				}
			} catch( Exception exc ) {
				report( exc );
			}

```
I wouln't call it a trivial solution..
Now compare it to the solution in Glib :)

---

### Post by Shin_Gouki2501 on 2008-02-24
you are my hero,

i noticed with the other project that you tend to use strange or more complicated solutions that actually needed:
[http://www.exampledepot.com/egs/java.io/CurDir.html](http://www.exampledepot.com/egs/java.io/CurDir.html)

;)

---

### Post by xlinuks on 2008-02-24
Please read my last post :) You didn't read it carefully, did you :)
If you're an experienced Java Developer you should understand why
 [http://www.exampledepot.com/egs/java.io/CurDir.html]("http://www.exampledepot.com/egs/java.io/CurDir.html")
doesn't always work.

---

### Post by Shin_Gouki2501 on 2008-02-24
well there are dozen of options to solve a single problem. So the scope or the factors which determine which solution to choose differ a lot.

since i don't know your problem or more your desired solution and towards which domain u works its hard to tell. Buts its alright. Good luck with glib and C++.

---


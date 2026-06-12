---
title: "java javax.imageio"
date: 2008-07-13
forum: Programming Talk
---

### Post by Atzu on 2008-07-13
I just made my first program using eclipse, I tried compile it using javac Program.java, and then run it using java Program but i get an error:

javax.imageio.IIOException: Can't read input file!


I believe the error is in here: 
```

try {
           sudoku = ImageIO.read(new File("src/icons/sudoku.png"));
           disabled = ImageIO.read(new File("src/icons/disabled.png"));
           selected = ImageIO.read(new File("src/icons/selected.png"));
        }
        catch(Exception e){
        	System.out.println(e);
        }

```
Any ideas? :(
Thanks in advance.

---

### Post by Shin_Gouki2501 on 2008-07-13
1. post the complete error message
2. post the complete code
3. check if ur path or file acutaly is correct

---

### Post by ceclauson on 2008-07-13
I'm guessing that Java's not finding one or all of your input files.  You could wrap each line of code in a try-catch block, and see which one or ones.

However, if your new to Java, you might not be aware that using the File constructor isn't the best way to access resource files.  The reason is that if you give a string that specifies a relative path, it takes as the base the current working directory of the operating system, and not the location of the binary that's running the code, as you might expect if you come from a C or C++ background.  The result is that you can't be sure that the File constructor will be able to find your resource file, and should probably only use this way of loading files if you have an absolute pathname.

The better way of loading resource files is to use the Class class's getResource() method.  It searches the directory of the binary that it's called on, and returns a URL to the resource (and if I remember right, I think it's null if it can't find it).  You can then use the URL to do whatever you want with the resource file.  Here's a sample code fragment that might do what you want to do:

```

BufferedImage sudoku = null;
BufferedImage disabled = null;
BufferedImage selected = null;

try {
	URL url = Program.class.getResource("sudoku.png");
	if(url == null) {
		throw new IOException("Couldn't load sudoku.png");
	}
	sudoku = ImageIO.read(url);

	url = Program.class.getResource("disabled.png");
	if(url == null) {
		throw new IOException("Couldn't load disabled.png");
	}
	disabled = ImageIO.read(url);

	url = Program.class.getResource("selected.png");
	if(url == null) {
		throw new IOException("Couldn't load selected.png");
	}
	selected = ImageIO.read(url);


} catch(IOException e) {
	System.err.println(e);
	return;
}

```

This code assumes that sudoku.png, disabled.png, and selected.png are all in that same directory as the binary Program.class.  You might experiment with passing getResource() a relative pathname.  It might work, but I've never tried it before, so I'm not sure.

---

### Post by tinny on 2008-07-13
Try statically using the full path to your files (e.g <path to src>/src/icons/disabled.png). This isn't the solution, but will tell you if you are having problems constructing your path dynamically.

---

### Post by xlinuks on 2008-07-13
Or just check programmatically - this will tell you for sure whether you specified correctly the path or not:
```

File f = new File( "src/icons/sudoku.png" );
if( f.exists() ) {
    sudoku = ImageIO.read( f );
} else {
    System.out.println( "Geee! I specified the wrong path to the image file!" );
}


```
As a side note, I don't know where you're accessing the images from, but try using "/src/icons/sudoku.png".

---

### Post by Atzu on 2008-07-13
Thanks, now my sudoku works :D. I think my problem was a little simple, all i did was move the images to where my java class where and now it works.

---

### Post by tinny on 2008-07-14
Good news. :)

Tip: "System.getProperty("user.dir");" will return the root path to your project. If I where you I would put the images in a folder within this root project path. (<project root>/img/)

E.g

```

        String separator = System.getProperty("file.separator");
        String rootPath = System.getProperty("user.dir");
        String imgPath = rootPath + separator + "img" + separator;
        ImageIcon image = new ImageIcon(imgPath + "sudoku.png");

```

Note: "file.separator" will get the file separator for the platform you are running your application on. e.g. Windows \, Linux /. This will make your application more platform independent.

---


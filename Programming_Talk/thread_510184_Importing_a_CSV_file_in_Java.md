---
title: "Importing a CSV file in Java"
date: 2007-07-26
forum: Programming Talk
---

### Post by welshboy on 2007-07-26
Hi guys,

I'm currently working on a program that needs to read in a CSV file in Java.  Now I've got the file to load properly, that's not a problem, and I've also got the data to be displayed, however it comes out as a list of memory addresses.  I've called the toString() method to try and format it but it still comes up as a load of memory addresses.

I would include the source code but I'm not sitting in front of my own computer yet.

The file has a series of records that I want to put into a Vector, so if anyone has any ideas about that too, then please let me know.  I did something like this years ago but I've long forgotten how to do it.

Any suggestions would be much obliged. 

welshboy

---

### Post by apoth on 2007-07-26
Can't really help with the memory addresses without seeing the source, depends what you've read the file into and what you're calling toString on.

I'd be inclined to use an array over a Vector in this instance - it sounds like you know how many records you want to store, so there's no need to have the Vector's ability to adapt to different lengths (extensibility?)

Generally if you need the extensibility I'd use an ArrayList instead of a Vector too - the difference is that a Vector is synchronised (i.e. you can safely play with it from different threads) which isn't functionality you'll often need and it has an associated performance cost.

Post the source when you get the chance and I (or someone else) should be able to be more helpful.

---

### Post by welshboy on 2007-07-26
Hi there,

Here is the source code for the program.

package emyrsoft.ambulance.control;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.nio.ByteBuffer;
import java.nio.channels.FileChannel;

/**
 * Class - File Loader
 * 
 * Class will provide loading functionality for the system.
 * 
 * @author Emyr Williams
 * @version First revision written on 26 Jul 2007
 */
public class FileLoader
{
	//private String filename;
	public void LoadFile(String filename)
	{
		File newFile = new File(filename);
		FileInputStream inFile = null;
		try
		{
			inFile = new FileInputStream(newFile);
		}
		catch(FileNotFoundException fnfe)
		{
			fnfe.printStackTrace(System.err);
			System.exit(1);
		}
		FileChannel inChannel = inFile.getChannel();
		ByteBuffer buf = ByteBuffer.allocate(48);
		
		try
		{
			while(inChannel.read(buf) != -1)
			{
				//String text = filename;
				//String [] records = text.split("[,/n/r]"); // rules for the tokenizing. 
				System.out.println("String read: " + ((ByteBuffer)(buf.flip())).asCharBuffer().toString().split("[,/n/r]"));
				buf.clear(); // clear buffer for the next read
			}
			System.out.println("EOF reached.");
			inFile.close(); // close the file and the channel.
		}
		catch(IOException e)
		{
			e.printStackTrace(System.err);
			System.exit(1);
		}
		System.exit(1);	
		
		// loading stuff in here.
		
		// also issue put the parser in here too which will add the records to
		// the vector.
		
	}
	
	public static void main(String args[])
	{
		FileLoader fl1 = new FileLoader();
		fl1.LoadFile("C:/Java/Ambulance/Manifest20070613.csv");
	}
}

Thanks, took a dash home to get it :D

---

### Post by welshboy on 2007-07-26
anyone?

---

### Post by apoth on 2007-07-26
The reason it looks like you're printing out a String is that it's a String array, returned by calling split() on a String. You'd have to loop through it to print out the Strings.

*But*, you're reading into a char buffer which I think is screwing up the character encoding so even if you fixed printing out each element in the array, you'd end up with a bunch of odd characters.

I'm going to take a guess that you don't need the nio libraries and would be better off with the normal io libraries (nio is very slightly quicker and a lot more complicated).

I'll post how I'd do it with the normal io libraries in a few minutes, if I'm wrong and you really did want the nio libraries I've not used them before so it'll take longer for me to figure out.

---

### Post by Geekkit on 2007-07-26
> **welshboy said:**
> anyone?

Try this:

[http://sourceforge.net/projects/csv4j/](http://sourceforge.net/projects/csv4j/)

---

### Post by Voynix on 2007-07-26
I guess it would be simpler to allocate the values into an array or a collection, but just out of curiosity I played with the charset encoding...

```
java.nio.channels.FileChannel inChannel = inFile.getChannel();
            fSize = inChannel.size();
            java.nio.ByteBuffer buf = java.nio.ByteBuffer.allocate((int) fSize);
            String message = "";
            try {
                while (inChannel.read(buf) != -1) {
                    ((ByteBuffer) (buf.flip())).asCharBuffer().toString();
                    java.nio.charset.Charset ascii = Charset.forName("US-ASCII");
                    java.nio.charset.CharsetDecoder toAscii = ascii.newDecoder();
                    java.nio.CharBuffer destination = toAscii.decode(buf);
                    StringTokenizer st = new StringTokenizer(destination.toString(), ",");
                    while (st.hasMoreTokens()){
                        message = st.nextToken();
                        System.out.println(message);
                    }
                    buf.clear();
                }
                java.lang.System.out.println("EOF reached.");
                inFile.close();
            } catch (java.io.IOException e) {
                e.printStackTrace(java.lang.System.err);
                java.lang.System.exit(1);
            }
            java.lang.System.exit(1);
```

---

### Post by apoth on 2007-07-26
```
import java.io.*;
import java.util.*;

public class ReadCSV {

	public void parse(String filename) {
		Collection<String> lines = new ArrayList<String>();
		try {
			BufferedReader br = new BufferedReader(new FileReader(
				new File(filename)
			));
			String line;
			while ((line = br.readLine()) != null) {
				lines.add(line);
			}
		} catch (Exception e) {
			e.printStackTrace();
		}
		printLines(lines);
		System.out.println("\n\n-----------------\n\n");
		printRecords(lines);
	}

	private void printLines(Collection<String> lines) {
		for (String line : lines) {
			System.out.println(line);
		}
	}

	private void printRecords(Collection<String> lines) {
		for (String line : lines) {
			String[] recordsOnLine = line.split(",");
			for (String record : recordsOnLine) {
				System.out.print(record +"|");
			}
			System.out.println();
		}
	}

	public static void main(String[] args) {
		new ReadCSV().parse("test.csv");
	}
}
```

That's how I probably would have done it.

---

### Post by welshboy on 2007-07-26
> **apoth said:**
> ```
import java.io.*;
import java.util.*;

public class ReadCSV {

	public void parse(String filename) {
		Collection<String> lines = new ArrayList<String>();
		try {
			BufferedReader br = new BufferedReader(new FileReader(
				new File(filename)
			));
			String line;
			while ((line = br.readLine()) != null) {
				lines.add(line);
			}
		} catch (Exception e) {
			e.printStackTrace();
		}
		printLines(lines);
		System.out.println("\n\n-----------------\n\n");
		printRecords(lines);
	}

	private void printLines(Collection<String> lines) {
		for (String line : lines) {
			System.out.println(line);
		}
	}

	private void printRecords(Collection<String> lines) {
		for (String line : lines) {
			String[] recordsOnLine = line.split(",");
			for (String record : recordsOnLine) {
				System.out.print(record +"|");
			}
			System.out.println();
		}
	}

	public static void main(String[] args) {
		new ReadCSV().parse("test.csv");
	}
}
```

That's how I probably would have done it.

Many thanks mate,

I'll get home and give it a go.  (I'm fixing the Vicar's computer at the moment!).

If I can get it to work, then when the final app is written, you will be credited.  I will also make sure you're credited in the class comments.  If that's ok.

Welshboy

---

### Post by trwww on 2007-07-31
Hi,

I know you asked for Java, but heres a fun way to do it in perl. You can use a csv file as a database table. Note that it accounts for commas embedded in the data, unlike the Java parsers that others in the thread posted.

Data file:

```
$ cat users
id,first,last,description
1,John,Doe,I live uptown
2,Sally,Smith,"I live uptown, too"
3,John,Adams,I WISH I lived uptown
```

Heres the program:

```
$ cat csv.pl
use warnings;
use strict;

use DBD::CSV;

my $dbh = DBI->connect("DBI:CSV:f_dir=./");

my $sql = 'select * from users order by last, first';
my $sth = $dbh->prepare( $sql );
$sth->execute;

while ( my $row = $sth->fetchrow_hashref ) {
  print "$row->{last}, $row->{first}: $row->{description}\n";
}
```

And heres the output:

```
$ perl csv.pl
Adams, John: I WISH I lived uptown
Doe, John: I live uptown
Smith, Sally: I live uptown, too
```

Whee :-)

---

### Post by welshboy on 2007-08-03
The only snag is it's for a customer that's using Vista, and it needs to be stand alone too, and believe it or not, I've started doing it all in C# at the moment, as I can't get the GUI quite right in Java.

If there's any interest in this, I'll keep you posted, and at some point, work out how to do it all in Java and post it on Sourceforge, but that depends if they want to keep the source code or not.

Have fun

welshboy :)

---


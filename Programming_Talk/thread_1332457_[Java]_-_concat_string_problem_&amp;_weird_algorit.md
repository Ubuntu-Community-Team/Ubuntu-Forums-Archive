---
title: "[Java] - concat string problem &amp; weird algoritm"
date: 2009-11-20
forum: Programming Talk
---

### Post by SpinningAround on 2009-11-20
EDIT: Notice the problem, forgot to save the changes :P still is there a better way to do this?

That is the problem with the programming but I'm suspecting that my method of choice is a little weird. What I'm doing is the following
run command "ifconfig | grep -m 1 'RX bytes' > file.txt"
read the file
get numbers from up and down

Question, is there a better way to do this?

Full code
```

	private static String fileInput(){
		File file = new File("file.txt");
		FileInputStream fis = null;
		BufferedInputStream bis = null;
		DataInputStream dis = null;
		String read="fail";

		try{
			fis = new FileInputStream(file);

			// Here BufferedInputStream is added for fast reading.
			bis = new BufferedInputStream(fis);
			dis = new DataInputStream(bis);
			read=dis.readLine();
			read=read.trim();
			
			// dispose all the resources after using them.
			fis.close();
			bis.close();
			dis.close();
		}
		catch (FileNotFoundException e){
			e.printStackTrace();
		}
		catch (IOException e){
			e.printStackTrace();
		}
		return read;
	}

	private static void getNum(String read){
		int i=0;
		char ca;
		String nr1=" ", nr2=" ",n;
		while(read.charAt(i)!=':'){
			i++;
		}
		i++;
		while(read.charAt(i)!=' '){
			ca = read.charAt(i);
			n=Character.toString(ca);
			nr1=nr1.concat(n); // don't work
			i++;
		}
		System.out.println(nr1); //return nothing (blank)
		while(read.charAt(i)!=':'){
			i++;
		}
		i++;
		while(read.charAt(i)!=' '){
			ca = read.charAt(i);
			n=Character.toString(ca);
			nr2=nr2.concat(n); // don't work
			i++;
		}
		System.out.println(nr2); //return nothing (blank)
	}


	public static void main (String args[]) throws IOException{
		String command = "ifconfig";
                Runtime shell = Runtime.getRuntime();
		shell.exec(command);
		String read = fileInput();
		getNum(read);
		}

```

Read part is from here [http://www.java-tips.org/java-se-tips/java.io/how-to-read-file-in-java.html](http://www.java-tips.org/java-se-tips/java.io/how-to-read-file-in-java.html)

EDIT:

To execute command ifconfig see this thread [http://ubuntuforums.org/showthread.php?t=1336402](http://ubuntuforums.org/showthread.php?t=1336402)

---

### Post by TennTux on 2009-11-20
In java there is a wonderful class java.lang.StringBuffer. This may be helpful for what your trying to do. See my example of StringBuffer:

```

private static final int	bufferSize	= 2048 ;
public String method(DataInputStream is) {
	StringBuffer	buffer	= new StringBuffer(bufferSize) ;
	String	line ;
	while ((line = dis.readLine) != null) {
		buffer.append(line.trim) ;
		buffer.append("\n") ;
	}

	return buffer.toString() ;
}

```

This code may not solve your complete problem but should give some help with the concatenation.

Best of luck.

---

### Post by TennTux on 2009-11-20
Looking at your code a little closer your getNum() could be changed to look like this.
```

	private static void getNum(String read) {
		int		index = 0 ;
		char		ca ;
		StringBuffer	nr1	= new StringBuffer(32) ;
		StringBuffer	nr2	= new StringBuffer(32) ;
		char[]		buffer	= read.toCharArray() ;
		
		// Find first ':'
		while ((index < buffer.length) && (buffer[index] != ':'))
			index++ ;
		// Skip ':'
		index++ ;
		// Collect nr1 value
		while((index < buffer.length) && (buffer[index] != ' '))
			nr1.append(buffer[index]) ;
		// Tell the world
		System.out.println(nr1.toString()) ;
		// Find next ':'
		while((index < buffer.length) && (buffer[index] != ':'))
			index++ ;
		// Skip ':'
		index++ ;
		// Collect nr2 value
		while((index < buffer.length) && (buffer[index] != ' '))
			nr2.append(buffer[index]) ;
		// Tell the world
		System.out.println(nr2.toString()) ;
	}

```

There are also other ways to approach this problem that involve String.indexof(':') and String.substring(from, to), however, you may not be ready for that just yet.

---


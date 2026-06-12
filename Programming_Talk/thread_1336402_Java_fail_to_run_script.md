---
title: "Java fail to run script"
date: 2009-11-24
forum: Programming Talk
---

### Post by SpinningAround on 2009-11-24
It's something weird with Java's way to run UNIX scripts, if I tell Java to run the script nothing happen, but if I run the script manually does it work. What on earth is wrong?

Script
```

ifconfig | grep -q ppp0
echo $? > VpnState.txt
exit 1

```

Java Code
```

	public static boolean Check(){
		String scriptPath = "/where/it/is";
		int status=1; //forced to change to return true
		shell(scriptPath); //jump of to the part that run the script
		String status = FileInOut.VpnRead(); //read VpnState.txt
		status=Integer.parseInt(status); //convert to an int
		return (status==0); // return true or false
	}

```

Shell Code
```
	
public static void shell(String path){
		try{
			Runtime comPrompt = Runtime.getRuntime();
			comPrompt.exec(path);
			Wait.oneSec();
		}
		catch (IOException e){
			System.out.println("Script Error " + e.getMessage());
		}
	}
```

Read, don't think there is any errors got an other similar that is working fine
```

	public static String VpnRead(){
		File file = new File(vpnPath);
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
			System.out.println(e.getMessage());
		}
		catch (IOException e){
			System.out.println(e.getMessage());
		}
		return read;
	}

```


Just in case, does this work?
```

while(Check())
//and
if(Vpn.Check())


```

---

### Post by doas777 on 2009-11-24
it may be that you are passing a multiline script as a string, with no semicolons. just a shot in the dark though.

---

### Post by SpinningAround on 2009-11-24
> **doas777 said:**
> it may be that you are passing a multiline script as a string, with no semicolons. just a shot in the dark though.

I tried to add ; to the file where the script is but it didn't work. Question is there a better way to execute the command 
ifconfig | grep -q ppp0
echo $? > VpnState.txt

?

---

### Post by SpinningAround on 2009-11-27
Don't anyone know? :( I don't know but might the problem be linked to that i'm using static in all my metods and is there a way to make them instaces?

---

### Post by Zugzwang on 2009-11-27
A question: Why do you go this detour through writing some stuff to a file? You can read the output of a spawned process directly. Here is an example: [http://mcoder.wordpress.com/2008/02/04/launch-a-process-from-java-and-wait-for-it-to-complete/](http://mcoder.wordpress.com/2008/02/04/launch-a-process-from-java-and-wait-for-it-to-complete/)

---

### Post by SpinningAround on 2009-11-27
> **Zugzwang said:**
> A question: Why do you go this detour through writing some stuff to a file? You can read the output of a spawned process directly. Here is an example: [http://mcoder.wordpress.com/2008/02/04/launch-a-process-from-java-and-wait-for-it-to-complete/](http://mcoder.wordpress.com/2008/02/04/launch-a-process-from-java-and-wait-for-it-to-complete/)

Wow looks nice, only one question. How do I get it to work? I don't really get how to use it, problem mainly with this part. Do I write a command or ?

```

Process process = Runtime.getRuntime().exec(args,null,new File(System.getProperty("user.dir")));

More specific

args,null,new File(System.getProperty("user.dir"))

```

---

### Post by Zugzwang on 2009-11-30
> **SpinningAround said:**
> I don't really get how to use it, problem mainly with this part. Do I write a command or ?


Ok, so let's take a look at the API. Obviously, it is this function that is being used:

[http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Runtime.html#exec(java.lang.String[],%20java.lang.String[],%20java.io.File)](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Runtime.html#exec(java.lang.String[],%20java.lang.String[],%20java.io.File))

So it looks like that the first parameter is where you put what you actually want to be called. In your case, you would probably need something like:
```

String[] cmd = {"/bin/sh", "-c", "ifconfig | grep -q ppp0"};

```

and then pass "cmd" as the argument. Here's some further information: [http://www.ensta.fr/~diam/java/online/io/javazine.html](http://www.ensta.fr/~diam/java/online/io/javazine.html)

---

### Post by SpinningAround on 2009-11-30
> **Zugzwang said:**
> Ok, so let's take a look at the API. Obviously, it is this function that is being used:

[http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Runtime.html#exec(java.lang.String[],%20java.lang.String[],%20java.io.File)](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Runtime.html#exec(java.lang.String[],%20java.lang.String[],%20java.io.File))

So it looks like that the first parameter is where you put what you actually want to be called. In your case, you would probably need something like:
```

String[] cmd = {"/bin/sh", "-c", "ifconfig | grep -q ppp0"};

```

and then pass "cmd" as the argument. Here's some further information: [http://www.ensta.fr/~diam/java/online/io/javazine.html](http://www.ensta.fr/~diam/java/online/io/javazine.html)
Sorry if I have upset you, thanks for all your help. It finally solved it didn't know that /bin/sh was needed.

---

### Post by Zugzwang on 2009-12-01
> **SpinningAround said:**
> Sorry if I have upset you, thanks for all your help. It finally solved it didn't know that /bin/sh was needed.

Sorry if it sounded like that. That was by no means the case. Oh, and if your problem is really gone please mark this thread as solved!

---

### Post by SpinningAround on 2009-12-02
I noticed that the program isn't working exactly as I thought. It looks like the program only read the first print. So if I run ifconfig followed with echo will it only catch ifconfig. I guess I can run ifconfig first then echo later but since I start a new shell everytime will I lose the info saved in the variables. Question is there a way to get around this or will I have to write the command to a file then read the file?

---

### Post by Zugzwang on 2009-12-02
I don't get it. If you want the return code of a command, you can use the return value of "Process.waitFor()". So you don't need that "echo" command.

---


---
title: "[java] Managing Multipule Streams"
date: 2008-06-24
forum: Programming Talk
---

### Post by Pyro.699 on 2008-06-24
Hello,

I have a script that is opening up "wget" several times, and i am displaying the output from each process in a separate JTextArea for each. Below is the code i have to run 3 of them, the problem i have is that it will only display the same amount of lines at a time, as in it waits for all 3 to be done line 1 to go onto line 2. How can i make it so that it will constantly check for updates and post them in the text area.

```

		Process p1 =  Runtime.getRuntime().exec("wget --progress=dot -x -i input[1].txt --directory-prefix=dls/");
		Process p2 =  Runtime.getRuntime().exec("wget --progress=dot -x -i input[2].txt --directory-prefix=dls/");
		Process p3 =  Runtime.getRuntime().exec("wget --progress=dot -x -i input[3].txt --directory-prefix=dls/");
		BufferedReader r1 =  new BufferedReader ( new InputStreamReader ( p1.getErrorStream () ) );
		BufferedReader r2 =  new BufferedReader ( new InputStreamReader ( p2.getErrorStream () ) );
		BufferedReader r3 =  new BufferedReader ( new InputStreamReader ( p3.getErrorStream () ) );
		int exit=0;

		while (exit != 1)
		{
			String l1,l2,l3;
			
			if ( (l1=r1.readLine()) != null){
				Home.addText(1, l1);
			}
			if ( (l2=r2.readLine()) != null){
				Home.addText(2, l2);
			}
			if ( (l3=r3.readLine()) != null){
				Home.addText(3, l3);
			}			
		}

```
Home.add(int,String) is a custom method that will append the code to the text area.

Thanks for your help
~Cody Woolaver

---

### Post by Zugzwang on 2008-06-25
First method: Use the ready() method of a BufferedReader to see if there's some more data (and only use .readLine() in this case). I'm not sure if that works.

Second (working) method: Use threads! I haven't checked the following example, but it works more of less like this:
[PHP]
class Updater extends Thread {

  private JTextArea dest;
  private BufferedReader reader,
  private bool done;

  public Updater(YourDestObject dest, BufferedReader reader) {
    this.dest = dest;
    this.reader = reader;
    done = false;
  }

  public void run() {
    String line = reader.readLine();
    while (line!=NULL) {
      dest.addText(line);
      line = reader.readLine();
    }
    done = true;
  }

  public bool isDone() { return done; }
}
[/PHP]

and then....
[PHP]
Process p1 =  Runtime.getRuntime().exec("wget --progress=dot -x -i input[1].txt --directory-prefix=dls/");
Process p2 =  Runtime.getRuntime().exec("wget --progress=dot -x -i input[2].txt --directory-prefix=dls/");
Process p3 =  Runtime.getRuntime().exec("wget --progress=dot -x -i input[3].txt --directory-prefix=dls/");
BufferedReader r1 =  new BufferedReader ( new InputStreamReader ( p1.getErrorStream () ) );
BufferedReader r2 =  new BufferedReader ( new InputStreamReader ( p2.getErrorStream () ) );
BufferedReader r3 =  new BufferedReader ( new InputStreamReader ( p3.getErrorStream () ) );
int exit=0;

Updater u1 = new Updater(Home1,r1);
Updater u2 = new Updater(Home2,r2);
Updater u3 = new Updater(Home3,r3);
u1.start();
u2.start();
u3.start();

while ((!u1.isDone()) || (!u2.isDone()) || (!u3.isDone()))
  Thread.yield();

[/PHP]

Change this code until it works for you and you're done!

---

### Post by Pyro.699 on 2008-06-25
Hello,

I have a few questions about the code and some of the variables and methods that you used.

**private JTextArea dest;** anything that involved a JTextArea is dealt in another file (Home.java), Home.java is the file that builds the entire GUI and has all the methods within it to manipulate the required fields.
**	  public Updater(YourDestObject dest, BufferedReader reader) {** Im not sure what my object type was, i was going to guess String but that is probally incorrect.
**	      dest.addText(line);** As stated in the first comment the file Home.java contains all the necessary information to manipulate the JTextArea's and the proper syntax is Home.addText(int x, String line) where x is the process number and the line is the line of text you want added.[/b]
**Updater u1 = new Updater(Home1,r1);** Im unsure why there is Home1-3 because Home is the main constructor in the file Home.java. Here is what that constructor looks like. (below)[/b]

```

	/**
	 * This is the default constructor
	 */
	public Home() {
		super();
		initialize();
	}

```

Thanks again for your help
~Cody Woolaver

---

### Post by issih on 2008-06-25
Using threads is indeed the best bet, however, swing actually has a nice little trick up its sleeve, look into the possibility of using the swingworker class, which would potentially manage your thread issues for you.

---

### Post by Zugzwang on 2008-06-25
> **Pyro.699 said:**
> Hello,

I have a few questions about the code and some of the variables and methods that you used.

**private JTextArea dest;** anything that involved a JTextArea is dealt in another file (Home.java), Home.java is the file that builds the entire GUI and has all the methods within it to manipulate the required fields.
**	  public Updater(YourDestObject dest, BufferedReader reader) {** Im not sure what my object type was, i was going to guess String but that is probally incorrect.
**	      dest.addText(line);** As stated in the first comment the file Home.java contains all the necessary information to manipulate the JTextArea's and the proper syntax is Home.addText(int x, String line) where x is the process number and the line is the line of text you want added.[/b]
**Updater u1 = new Updater(Home1,r1);** Im unsure why there is Home1-3 because Home is the main constructor in the file Home.java.[/b]


The structure of your GUI classes was not visible in the post you wrote (except for the first case - Here I made a mistake) You can modify the updater class in order to work with only one "Home" object but storing the index to be passed to Home.addText(). That was what was meant by "Change this code until it works for you and you're done!".

By the way, I forgot to mention that every GUI modification should be carried out by the GUI thread, so:
[PHP]

class Updater extends Thread {

  private Home dest;
  private int index;
  private BufferedReader reader;
  private boolean done;

  public Updater(Home dest, int index, BufferedReader reader) {
    this.dest = dest;
    this.reader = reader;
    this.index = index;
    done = false;
  }

  public void run() {
    try {
      String line = reader.readLine();
      while (line!=null) {
          final String temp = line;
          SwingUtilities.invokeLater(new Runnable() {
            public void run() {
              dest.addText(index, temp);
            }
          });
          line = reader.readLine();
      }
      done = true;
    } catch (java.io.IOException e) {
      // Handle however you like!
      throw new RuntimeException(e);
    }
  }

  public boolean isDone() { return done; }
}  
[/PHP]

If "addText" is a static method of the "Home" class that you can of course drop that from the constructor. Changing the other code fragment is left as an excercise. However, look into issih's suggestion, I didn't know about that class.

---

### Post by Pyro.699 on 2008-06-25
Thanks alot, that works perfectly :) One last question, this should work right?

```

if(u1.isDone()) Home.isEnabled(1, false); Home.changeColor(1, Color.RED);
			if(u2.isDone()) Home.isEnabled(2, false); Home.changeColor(2, Color.RED);
			if(u3.isDone()) Home.isEnabled(3, false); Home.changeColor(3, Color.RED);

```(this is inside the while tag)

What should happen is when the processes finish, it will run the two custom scripts correct? isDone will make the textarea readOnly and changeColor will make the textarea red.

---

### Post by Zugzwang on 2008-06-26
> **Pyro.699 said:**
> Thanks alot, that works perfectly :) One last question, this should work right?

```

if(u1.isDone()) Home.isEnabled(1, false); Home.changeColor(1, Color.RED);
			if(u2.isDone()) Home.isEnabled(2, false); Home.changeColor(2, Color.RED);
			if(u3.isDone()) Home.isEnabled(3, false); Home.changeColor(3, Color.RED);

```(this is inside the while tag)


First of all, you forgot the braces, so it should be:
```

if(u1.isDone()) {
  Home.isEnabled(1, false); 
  Home.changeColor(1, Color.RED);
}

if(u2.isDone()) {
  Home.isEnabled(2, false); 
  Home.changeColor(2, Color.RED);
}

if(u3.isDone()) {
  Home.isEnabled(3, false); 
  Home.changeColor(3, Color.RED);
}

```
...and then, you have to 
[LIST]
[*]Check if you already changed the color to RED before doing so in order to avoid flickering (that might occur on some systems depending on the configuration) and high system load since that is done repeatedly over and over again.
[*]Execute this code both *in* the while loop and *after* the while loop since you might miss some completion in the loop but when the computer resches the evaluation of the while clause, the thread might have finished.
[/LIST]execute this code 

All in all, it would be better if you add such code to the run() method of the "Updater" class itself since that solves both problems.

---

### Post by Pyro.699 on 2008-06-26
I actually found a much easier way of doing this (implementing your methods). To be honest with you there is actually 20 instances of this script running and as such there was ALOT of copy-paste and alot of code that if a small change was required was alot of work. I thought... why not use arrays.

```

Process[] p = new Process[20];
        BufferedReader[] r = new BufferedReader[20];
        Updater[] u = new Updater[20];
        Boolean[] d = new Boolean[20];
        
        for(int i=1;i<=20;i++){
    p[i-1] = Runtime.getRuntime().exec("wget -i input"+i+".txt");
                 r[i-1] =  new BufferedReader ( new InputStreamReader ( p[i-1].getErrorStream () ) );
                 u[i-1] = new Updater(r[i-1],i);
                 u[i-1].start();
                 d[i-1] = false;
        }

```
and then
```

        while(x!=1){
            for(int i=1;i<=20;i++){
                if(u[i-1].isDone() && d[i-1]==false){
                    Home.isEnabled(i, false);
                    Home.changeColor(i, new Color(255,102,102));
                    log("process is done");
                    d[i-1]=true;
                }
            }
            for(int i=1;i<=20;i++){
                if(d[i-1]==true){
                    x=1;
                }else{
                    x=0;
                    break;
                }
            }
            Thread.yield();
        }

```

Thanks again, you've been alot of help
~Cody Woolaver

---


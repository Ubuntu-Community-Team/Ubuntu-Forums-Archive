---
title: "NoClassDefFoundError"
date: 2011-01-04
forum: Programming Talk
---

### Post by alexmoca on 2011-01-04
Hi everybody!

When I run this program in Netbeans, a NullPointerException is thrown. Maybe this is expectable [please correct me if I'm wrong], since my application is meant to be run in a terminal.

However, when I manually run my code [javac the below classes and then java Main], I get a NoClassDefFoundError.

Short description: Main only instantiates Engine. Engine instantiates Terminal and tries to read some user input using methods from the instance of Terminal.

Main.java
```

package example;
public class Main {

    public static final double appVersion = 0.1;
    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
        Engine e = new Engine();
    }

}
```

Terminal.java
```

package example;
/**
 * This class handles all the input and output of the console.
 */
public class Terminal {
    Console c;
    String username;
    String password;

    /**
     * Class constructor.
     * Will instantiate a Terminal object that will read the user input.
     */
    public Terminal() {
        c = System.console();
    }

    /**
     * Reads the username from the console.
     * @throws NullPointerException
     */
    public void readUsername() throws NullPointerException {
        username = c.readLine();
    }

    /**
     * Reads the password from the console.
     * @throws NullPointerException
     */
    public void readPassword() throws NullPointerException {
        password = c.readLine();
    }
}

```

Engine.java
```

package example;
/**
 * This class is the brain of the application. It controls the user input,
 * matches the command, establishes connections, sends input etc.
 */
public class Engine {
    public Engine() {
        Terminal t = new Terminal();

        // Handles username reading.
        try {
            t.readUsername();
        } catch(NullPointerException e) {
            System.err.println("Application must be run from terminal");
        }
        
        // Handles password reading.
        try {
            t.readPassword();
        } catch(NullPointerException e) {
            System.err.println("Application must be run from terminal");
        }
    }
}

```

---

### Post by dwhitney67 on 2011-01-04
All of your Java classes are being placed into a package called "example".  Thus I assume that you have a directory (folder) called *example*, and within it you have Engine.java, Main.java, Terminal.java and their corresponding .class files after invoking javac.

To run your application from the terminal, you need to change your working directory to be at the same level as *example*; so if *example* is in */home/user*, then you need to be at */home/user* to invoke:
```

java example.Main     # that's "java example dot Main"

```

---

### Post by alexmoca on 2011-01-09
Thank you, dwhitney67! It is a bit weird since I remember running my application from the same directory [package] it was in. So I've been using java Main instead of java example.Main if I remember well.

---

### Post by slavik on 2011-01-09
noclassdeffound exception is thrown when the class loader cannot locate the reuqested class in any jar in the class path.

---


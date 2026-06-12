---
title: "Can't Compile Java Servlets"
date: 2007-10-15
forum: Programming Talk
---

### Post by Nergar on 2007-10-15
Hello 

first things first, im in the middle of my class (college not java) so if i can get fast support it would be great!!

Im learning java in college but unlike all the other students, im coding in Ubuntu. The problem i have is i can compile any java program without any problems but i can't compile any Servlets 

Heres my code:

```
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class Welcome extends HttpServlet {

	public void doPost(HttpServletRequest request,
						HttpServletResponse response)

		throws ServletException, IOException {

			/*
			 *
			 * indica el tipo de contenido (por ejemplo, text/html), que sera regresado
			 * como respuesta
			 *
			 */
			response.setContentType("text/plain");

			/*
			 * Regresa un flujo de salida utilizado
			 * para enviar datos al cliente
			 */

			PrintWriter out = response.getWriter();

			/*
			 * 	Escribe respuesta
			 */

			out.println("Bienvenido a UVM!");
		}
}
```

and here is the javac output

```
nergar@ubuntu-lap:~$ javac Documents/College/Introduccion\ a\ Sistemas/Welcome/Welcome.java 
----------
1. ERROR in Documents/College/Introduccion a Sistemas/Welcome/Welcome.java (at line 2)
        import javax.servlet.*;
               ^^^^^^^^^^^^^
The import javax.servlet cannot be resolved
----------
2. ERROR in Documents/College/Introduccion a Sistemas/Welcome/Welcome.java (at line 3)
        import javax.servlet.http.*;
               ^^^^^^^^^^^^^
The import javax.servlet cannot be resolved
----------
3. ERROR in Documents/College/Introduccion a Sistemas/Welcome/Welcome.java (at line 5)
        public class Welcome extends HttpServlet {
                                     ^^^^^^^^^^^
HttpServlet cannot be resolved to a type
----------
4. ERROR in Documents/College/Introduccion a Sistemas/Welcome/Welcome.java (at line 7)
        public void doPost(HttpServletRequest request,
                           ^^^^^^^^^^^^^^^^^^
HttpServletRequest cannot be resolved to a type
----------
5. ERROR in Documents/College/Introduccion a Sistemas/Welcome/Welcome.java (at line 8)
        HttpServletResponse response)
        ^^^^^^^^^^^^^^^^^^^
HttpServletResponse cannot be resolved to a type
----------
6. ERROR in Documents/College/Introduccion a Sistemas/Welcome/Welcome.java (at line 10)
        throws ServletException, IOException {
               ^^^^^^^^^^^^^^^^
ServletException cannot be resolved to a type
----------
6 problems (6 errors)
```

---

### Post by CptPicard on 2007-10-15
You're missing the Servlet API... grab a servlet.jar from somewhere, probably Sun :)

Here --> [http://java.sun.com/products/servlet/](http://java.sun.com/products/servlet/)

---

### Post by Nergar on 2007-10-15
Pardon my ignorance but what do i do with it?
Do i just "java servlet.jar" it?
And what does it has to do with javac?
:S

---

### Post by CptPicard on 2007-10-15
Hmm. What are you using to code your Java stuff in Ubuntu with? An IDE or just the command line? An IDE makes this easier, but let's assume you're going commando...

You need to have it in your classpath. Either you make an environment variable 

```

export CLASSPATH=$CLASSPATH:/path/to/servlet.jar

```

(stick into your ~/.bash_profile to make permanent)

or explicitly tell about it to javac

```

javac -cp $CLASSPATH:/path/to/servlet.jar YourSource.java

```

---

### Post by Nergar on 2007-10-15
I used to use Netbeans, but i recently discovered Geany its amazing!
Ok, thanks for the suggestion i will try it,

My class ended so ill try when i get home

just another question, can i use tomcat as a servlet???

---

### Post by CptPicard on 2007-10-15
Tomcat is a server you host your servlets on... as parts of a web app.

---

### Post by Nergar on 2007-10-16
OK I finally got it! Thanks for the help

So here is what I did:

I downloaded Workbench (iCarnegie servlet) and unzipped it in /opt so I could use it
I set my environmental variables in /etc/profile
```
export CLASSPATH=/opt/wb/workbench.jar
export WORKBENCH_HOME=/opt/wb
export JAVA_HOME=/usr
export PATH=$PATH:$JAVA_HOME:$CLASSPATH:$WORKBENCH_HOME
```
Then I had to 
```
sudo update-alternatives --config java
sudo update-alternatives --config javac
```
because I was using the eclipse compiler and the gnu Java instead of Sun's

It took me several hours to figure all out but I did it. Hope this helps if someone has the same problem.

---


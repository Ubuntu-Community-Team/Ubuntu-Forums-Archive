---
title: "Java + Ubuntu Commands"
date: 2008-03-15
forum: Programming Talk
---

### Post by midnightray on 2008-03-15
My first non uni and app. Basically installed php, mysql and apache from the repo's and wanted a gui to stop/start apache/mysql like XAMPP.

Ok after googling and playing around with netbeans. I have found this method of running commands through Java.

```
    
    private String SHELL = "gnome-terminal";
    private String SHELL_PARAM ="-e";

//Method to execute commands
public void doAction(String command,String servicename, String actionname){
        ProcessBuilder launcher = new ProcessBuilder();
        Map<String, String> environment = launcher.environment();
        launcher.redirectErrorStream(true);
        launcher.command(SHELL,SHELL_PARAM,command);
        
        Process p;
        String lines;
        try {
            p = launcher.start();
            p.waitFor();
            BufferedReader is = new BufferedReader(
                    new InputStreamReader(p.getInputStream()));
            
            BufferedReader err = new BufferedReader(
                    new InputStreamReader(p.getErrorStream()));
            
            String errMsg = "";
            while ((lines = is.readLine()) != null) {
                errMsg += lines + "\n";
            }
            
            while ((lines = err.readLine()) != null) {
                errMsg += lines + "\n";
            }
            setStatusText(errMsg);
            setStatusText(servicename + " " + actionname + "...");
        } catch (Exception ex) {
            ex.printStackTrace();
        }
    }

//method called from action listeners placed by netbeans like e.g.
// doAction("sudo /etc/init.d/apache2 stop", "apache", "stopped");
// last 2 params are for a message to be put in a text area,
// setting text area is a method, not included but a simple .setText()


```


The only really things I would like is, is there a way to get the full screen password box like when accessing admin stuff.

Can Java be themed to match Ubuntu's default human theme, it looks horrible really.

---

### Post by smartbei on 2008-03-15
Maybe using gksudo...

---

### Post by midnightray on 2008-03-15
That works great, starting to think Java isn't so bad for writing little apps in.

But how can I make it look pretty like Gnome ? :)

edit: after googling

try{
UIManager.setLookAndFeel(
	    "com.sun.java.swing.plaf.gtk.GTKLookAndFeel");
}catch(Exception e{
}

works great!

---

### Post by themusicwave on 2008-03-15
Java does support changing the Theme from Swing to a more native theme.

I don't like how Swing looks by default, the only benefit it has is that it will be consistent on all platforms.  I usually use a native look and feel.

Here is a Sun article about setting look and feel.  [http://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/plaf.html]("http://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/plaf.html")


As for the sudo thing.  Either rn the program with gksudo java program or maybe run a system command like this:

gksudo cat /dev/core that will force a gksudo popup.  I think generally this is considered a bad thing though, programs aren't usually supposed to elevate themselves.

---


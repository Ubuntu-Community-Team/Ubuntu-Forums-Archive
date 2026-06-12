---
title: "java stderr listener"
date: 2009-06-27
forum: Programming Talk
---

### Post by djbushido on 2009-06-27
I am wanting to create a listener for the stderr stream that will catch any text on the stream and then output this as a message dialog. I can do the dialog, trying to catch the output of stderr and redirecting it to a dialog is a problem.
What I would like is to have something like the Scanner object, only for stderr, not stdin. Also, I would like to catch and redirect the stderr stream, rather than just catching and outputting. To explain, when a function outputs to stderr, if it was running in a console, that the console would not show the output stream. However, if this is not possible, I can get over it.

---

### Post by Reiger on 2009-06-27
You can sandbox your main application in a slave process and have its parent container/monitor process read from stderr/stdout as appropriate.

Alternatively, I don't know whether you can influence the System.err and System.out stream (you can close them, but replacing them with something else?); and of course you can decide NOT to print to System streams, but rather use your own [static] object (global variables) over which you have full control.

---

### Post by djbushido on 2009-06-27
No, I meant just something to listen to the stderr stream. We were attempting to have one package as terminal and one as gui. Thus the terminal would output to stderr, and the gui would catch it and redirect it to something a user would be able to see.

---

### Post by Reiger on 2009-06-27
Like I said in that case have the GUI sandbox the terminal app.

---

### Post by pbrockway2 on 2009-06-27
> **djbushido said:**
> No, I meant just something to listen to the stderr stream. We were attempting to have one package as terminal and one as gui. Thus the terminal would output to stderr, and the gui would catch it and redirect it to something a user would be able to see.

Rather than *listening* to stderr (whatever that means exactly) you could create your own print stream that writes bytes by printing stuffto a gui component.  Then you set System.err to be your new print stream.

Without worrying about threading and stuff (it is really just meant to answer the question raised above about setting the stream used as System.err)

```

import java.io.IOException;
import java.io.OutputStream;
import java.io.PrintStream;

import javax.swing.JFrame;
import javax.swing.JScrollPane;
import javax.swing.JTextArea;

public class ErrGui {
    public static void main(String[] args) {
        System.setErr(new PrintStream(new GuiOutputStream()));
        int foo = 1 / 0;
    }
}

class GuiOutputStream extends OutputStream {
	
    private JTextArea ta;
	
    public GuiOutputStream() {
        ta = new JTextArea(20, 100);
        JFrame frame = new JFrame("Error");
        frame.add(new JScrollPane(ta));
        frame.pack();
        frame.setVisible(true);
    }

    @Override
    public void write(int b) throws IOException {
        ta.append("" + (char)b);
    }
}

```

---

### Post by djbushido on 2009-06-29
So what you are saying is that the gui redirects the stderr stream to itself?
I am a bit confused, also on what is meant by sandboxing the app.

---

### Post by Reiger on 2009-06-30
Your GUI basically should spawn a child process for the terminal app. It can then read from the terminal app's stdout/stderr and write to its stdin.

You must put it in a sandbox in the sense that the terminal app might crash/die and your GUI app should take care to restore lost work / respawn the child process.

---

### Post by cdiem on 2009-06-30
Edit - nevermind.

---


---
title: "Help with Java save file dialog"
date: 2011-04-08
forum: Programming Talk
---

### Post by skytreader on 2011-04-08
I'm trying to make a JFileChooser (in its save file dialog incarnation) write to a directory specified by the user. But my efforts are futile and it keeps ending up in the directory where my package is.

Here's my ActionListener:

```

private JFileChooser SaveDialog = new JFileChooser();

private class ExportLogListener implements ActionListener{
		JTextArea TargetOutput;
		Component parent;
		
		public ExportLogListener(JTextArea TargetOutput, Component parent){
			this.TargetOutput = TargetOutput;
			this.parent = parent;
		}
		
		public void actionPerformed(ActionEvent ae){
			try{
				int foo = SaveDialog.showSaveDialog(parent);
				
				if(foo == JFileChooser.APPROVE_OPTION){
					String path = SaveDialog.getCurrentDirectory().getName();
					System.out.println(path);
					String filename = SaveDialog.getSelectedFile().getName();
					System.out.println(filename);
					PrintWriter pw = new PrintWriter(new BufferedWriter(new FileWriter(filename)));
					pw.println(TargetOutput.getText());
					TargetOutput.write(pw);
					pw.close();
					System.out.println("PrintWriter closed.");
				}
			}
			catch(IOException ioe){
				System.out.println("ioe occurred!");
			}
		}
	}

```

Any hints?

---

### Post by r-senior on 2011-04-08
getSelectedFile() returns a java.io.File.

From [http://download.oracle.com/javase/6/docs/api/java/io/File.html](http://download.oracle.com/javase/6/docs/api/java/io/File.html)
```

public String getName()

Returns the name of the file or directory denoted by this abstract
pathname. [COLOR="Red"]This is just the last name in the pathname's name
sequence[/COLOR]. If the pathname's name sequence is empty, then the empty
string is returned.

```

Have a look at the absolutePath() method and see if that does the job.

---

### Post by skytreader on 2011-05-15
> **r-senior said:**
> 

Have a look at the absolutePath() method and see if that does the job.

Sorry for the very late update but case closed. Though I think that should be *get*AbsolutePath() ?

[http://download.oracle.com/javase/6/docs/api/java/io/File.html#getAbsolutePath(](http://download.oracle.com/javase/6/docs/api/java/io/File.html#getAbsolutePath())

Thanks!

---


---
title: "carriage returns in java from mysqldump"
date: 2007-04-26
forum: Programming Talk
---

### Post by th3james on 2007-04-26
Hi Guys

Im trying to get a java app to backup a database. I can get it to write a script to a text file using this command:

mysqldump --allow-keywords --opt -uroot -psql databasename > backup.sql

however, the problem is that the backup.sql ends up as 1 long line without any new lines. i understand this is something to do with the way *nix handles carriage returns. How can i work round this?
here is the code im using
```

Runtime runtime = Runtime.getRuntime();
	            Process proc = runtime.exec(
	                "mysqldump --allow-keywords --opt -uroot -psql databasename");
	            InputStream inputstream =
	                proc.getInputStream();
	            InputStreamReader inputstreamreader =
	                new InputStreamReader(inputstream);
	            BufferedReader bufferedreader =
	                new BufferedReader(inputstreamreader);
	    
            // output to file
	            int returnVal = backupFileChooser.showOpenDialog(GUIControl.mainframe);
	            
                    if (returnVal == JFileChooser.APPROVE_OPTION) {
		            File file = backupFileChooser.getSelectedFile();
		            outputStream = new FileWriter(file.getPath());
		            System.out.println(file.getPath());
		       
		            String line;
		            while ((line = bufferedreader.readLine()) 
		            		!= null)
		            {
		            	outputStream.write(line);
		            }
		            outputStream.close();
	            }

```

This code is part of a computer science project, and will be run on a windows machine when it is marked, will it work fine on a windows box?

any help hugely appreciated

thanks
James

---

### Post by phossal on 2007-04-26
What is that code doing?

---

### Post by th3james on 2007-04-27
Sorry, i forgot 1 line at the begining (was incredibly tired when i wrote it....), should all be preceded by
```
FileWriter outputStream;
						try
						{
```
and obviously the closing of the try statement after

what the code is doing is running the command
 "mysqldump --allow-keywords --opt -uroot -psql databasename"

then reading what the command returns to the standard input (which is the database creation script code). it then opens a file chooser where the user specifies a file to write to. The code that has been returned is then written to that file, the only problem is, its all on 1 line, instead of many.

I really just need to know if i will have this problem in windows, where i thort new line characters are handled differntly

sorry for being unclear

thanx,,
james

---

### Post by gario on 2007-04-27
The problem is that you are reading in the mysqldump output one line at a time (which strips off the trailing newlines and/or CRs), but then writing out the output to a file without adding the line separators back in.

You could use a PrintWriter, then call ```
PrintWriter.println(line)
``` to output each line.  This will automatically append the platform specific line separator to each line of output.

Or you could manually do this by adding the line separator to each line you output:

```

String lineSep = System.getProperty("line.separator");
...
outputStream.write(line + lineSep);

```

---


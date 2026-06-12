---
title: "(java)JFileChooser save dialog question"
date: 2008-10-19
forum: Programming Talk
---

### Post by HotCupOfJava on 2008-10-19
Hello all - I've been hunting around to see if anyone has seen a version of the swing JFileChooser that will do automatic filename extensions (.txt, .java, etc.). I found a post where someone asked the team at Sun about this, and they basically said "we're not gonna do that anytime soon". I was wondering if anyone has extended the code themselves for this feature. I'm toying with the idea of writing one myself (I consider myself a "low-intermediate" java programmer). If I end up writing a class that extends JFileChooser, I'll probably use a JCheckBox to let the user select whether they want the extension or not. I'll get the extension from whatever FileFilter is selected (and disable it if no filters are selected or available). But I thought I'd check around before I "reinvented the wheel". 

Thanks

---

### Post by srujan on 2008-10-19
i guess u cud do dat......but i feel its too small a project to make any difference...

---

### Post by drubin on 2008-10-19
You do not need to extend it. You can use a filter. (See below).
You should be able to work out how to add other extentions. 
[PHP]
JFileChooser  fc = new JFileChooser();

            fc.setAcceptAllFileFilterUsed(false);

            fc.setFileFilter(new FileFilter(){

               public boolean accept(File path){

                  return (path.isDirectory() ||

                        path.getAbsolutePath().endsWith(".java"));

               }

               public String getDescription(){

                  return "Java files *.java";

               }

            });
[/PHP]

---

### Post by drubin on 2008-10-19
> **srujan said:**
> i guess u cud do dat......but i feel its too small a project to make any difference...

NO project is to small to experiment and learn new things.

---

### Post by HotCupOfJava on 2008-10-19
> **drubin said:**
> You do not need to extend it. You can use a filter. (See below).
You should be able to work out how to add other extentions. 
[PHP]
JFileChooser  fc = new JFileChooser();

            fc.setAcceptAllFileFilterUsed(false);

            fc.setFileFilter(new FileFilter(){

               public boolean accept(File path){

                  return (path.isDirectory() ||

                        path.getAbsolutePath().endsWith(".java"));

               }

               public String getDescription(){

                  return "Java files *.java";

               }

            });
[/PHP]

Well - I'm not trying to add file filters to affect what will be displayed - I'm trying to make it automatically append the correct extension to the filename typed in the "save" dialog (which would be determined by what filter is selected).

---

### Post by geirha on 2008-10-20
Isn't it easier to do something like
```

   JFileChooser fc= new JFileChooser();
   JCheckBox cb= new JCheckBox("Automatically append extention");
   fc.setAccessory(cb);

```
And then check cb.isSelected() after a file has been selected?

---

### Post by HotCupOfJava on 2008-10-20
> **geirha said:**
> Isn't it easier to do something like
```

   JFileChooser fc= new JFileChooser();
   JCheckBox cb= new JCheckBox("Automatically append extention");
   fc.setAccessory(cb);

```
And then check cb.isSelected() after a file has been selected?

Well - yes, that probably would be easier......I'm showing my ignorance - I wasn't aware of the setAccessory method.....I'll have to look into that.

---

### Post by HotCupOfJava on 2008-11-08
OK - I've gotten this fixed like I like. I DID end up extending the JFileChooser (I'll be writing other apps that need to do this, so I went ahead with it). BUT - I did use the setAccessory method as well. Then I had to have the save dialog get the extension from the filter to append it to the filename. This was a problem because the getExtensions method returns an array. I ended up doing this: getExtensions()[0], which works OK if you only have one type of file in the FileNameExtensionFilter. If I ever want it to do the same with more choices I'll have to come up with something else. The graphical component for the file filters on the JFileChooser looks like a combo box, so I was hoping to extend the JFileChooser to use something like getSelectedIndex to help me select which array element I wanted from the FileNameExtensionFilter.getExtensions(), but I've dug through the source and can't find the thing!

---

### Post by AnotherOswald on 2008-11-26
Hey HotCupOfJava,

I am looking to auto extend every file I save with ".txt". I think the case is similar or identical to yours. Am i correct?

You say you have found a solution. Is it a very cumbersome process or straight forward?

Would you mind explaining in a more detailed manner maybe with the code? I am a novice so it might not make sense otherwise.

thanks in advance!
oswald

---

### Post by AnotherOswald on 2008-11-26
This below is not my solution but it works so I am attaching it here for future reference to people who will need it:


"For example, entering "foo" will result in "foo.txt", but "foo.java" will result in "foo.java"."
---------------------

File file = chooser.getSelectedFile();
String name = file.getName();
if (name.indexOf('.')==-1) {
   name += ".txt";
   file = new File(file.getParentFile(), name);
}
// Now "file" will always have some extension, defaulting to .txt
return file;

----------------------

---

### Post by drubin on 2008-11-26
> **AnotherOswald said:**
> This below is not my solution but it works so I am attaching it here for future reference to people who will need it:


"For example, entering "foo" will result in "foo.txt", but "foo.java" will result in "foo.java"."
---------------------

File file = chooser.getSelectedFile();
String name = file.getName();
if (name.indexOf('.')==-1) {
   name += ".txt";
   file = new File(file.getParentFile(), name);
}
// Now "file" will always have some extension, defaulting to .txt
return file;

----------------------
Just know that that code does not create the file on the disk. It just creates a reference to it. So if I type  foo it will be foo.txt but if I select foo.java that file will already exist on the disc drive. 

Just remember to check if the file exists before using it for things.

---

### Post by HotCupOfJava on 2009-02-03
Wow, it has been a while since I have checked up on this thread. I apologize, I should have done this much sooner. Here is my solution, which is an overide of the JFileChooser class:

```
/**
* This version of the JFileChooser was designed to allow the user
* to have an automatic filename extension added when the "save"
* dialog box is shown. This will employ a JCheckBox. If the option is selected,  
* the intention is for the selected filefilter to be the extension. If no filters are 
* selected, the JCheckBox will be disabled
*/
import java.awt.*;
import javax.swing.*;
import javax.swing.filechooser.*;
import java.io.*;

public class MyFileChooser extends JFileChooser{

	public MyFileChooser(){
		super();
		initJCheckBox();
		this.setAccessory(fileNameExtensionCheckBox);
		
	}
	public MyFileChooser(File currentDirectory, FileSystemView fsv){
		super(currentDirectory, fsv);
		initJCheckBox();
		this.setAccessory(fileNameExtensionCheckBox);
	}
	public MyFileChooser(File currentDirectory){
		super(currentDirectory);
		initJCheckBox();
		this.setAccessory(fileNameExtensionCheckBox);
	}
	public MyFileChooser(FileSystemView fsv){
		super(fsv);
		initJCheckBox();
		this.setAccessory(fileNameExtensionCheckBox);
	}
	public MyFileChooser(String currentDirectoryPath){
		super(currentDirectoryPath);
		initJCheckBox();
		this.setAccessory(fileNameExtensionCheckBox);
	}
	public MyFileChooser(String currentDirectoryPath, FileSystemView fsv){
		super(currentDirectoryPath, fsv);
		initJCheckBox();
		this.setAccessory(fileNameExtensionCheckBox);
	}
	//Here is the code for initializing the JCheckBox
	public void initJCheckBox(){
		fileNameExtensionCheckBox = new JCheckBox("automatic file name extension");
		fileNameExtensionCheckBox.setVisible(false);
		fileNameExtensionCheckBox.setEnabled(false);
	}
	//overriden method from superclass
	protected JDialog createDialog(Component parent) throws HeadlessException {
        		JDialog dialog = super.createDialog(parent);
		if (this.getDialogType()==SAVE_DIALOG){
			fileNameExtensionCheckBox.setVisible(true);
			fileNameExtensionCheckBox.setEnabled(true);
			
		}
          		return dialog;
    	}
	//overriden method from superclass
	public File getSelectedFile(){
		File f = super.getSelectedFile();
		if (this.getDialogType()==SAVE_DIALOG){
			if (fileNameExtensionCheckBox.isSelected()){
				String path = f.getPath();
				FileNameExtensionFilter ff =(FileNameExtensionFilter) this.getFileFilter();
				return new File(path+"."+ff.getExtensions()[0]);
			}
			else{
				return f;
			}
		}
		else{
			return f;
		}
	}

	//the following item is the graphical control to add a filename   extension
	private JCheckBox fileNameExtensionCheckBox;
}
```

Maybe this will help someone.

---

### Post by drubin on 2009-02-04
> **HotCupOfJava said:**
> Wow, it has been a while since I have checked up on this thread. I apologize, I should have done this much sooner. Here is my solution, which is an overide of the JFileChooser class:

Maybe this will help someone.

Thanks sure it will  :)

---

### Post by mmmmario on 2009-06-27
```

FileNameExtensionFilter ff =(FileNameExtensionFilter) this.getFileFilter();

```
Can fail, because current selected FileFilter can be "show all files" witch is not instance of FileNameExtensionFilter.

To fix this use this code:
```

if(getFileFilter() instanceof FileNameExtensionFilter){
  FileNameExtensionFilter ff =(FileNameExtensionFilter) getFileFilter();
}else{
  // do not add default extension
}

```

---


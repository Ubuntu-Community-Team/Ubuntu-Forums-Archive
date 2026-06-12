---
title: "HOWTO: Set up Laszlo in the Eclipse Environment"
date: 2005-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by bored2k on 2005-06-03
This was posted by [l.tambiah](http://ubuntuforums.org/journal.php?do=showentry&e=259) on his blog. I just copied it here for more visibility.

[QUOTE=l.tambiah]Package Requirements


J2SE Development Kit (JDK) 5.0 update 3

Eclipse 3.0.2

Mozilla -1.6

You require mozilla to make the preview work. You must also install flash in the mozilla browser. Firefox will not work!!!

openlaszlo-3.0

laszloIDE 2.0


Java Environment

1.Install the J2SE Development Kit (JDK) 5.0 update 3

2.Set the classpath (i take it you know how to do that).

Linux Install Considerations For Laszlo and Eclipse

The Visual Editor uses the SWT Browser control, which requires Linux users to install Eclipse 3.02 and Mozilla 1.6.x (Note: Mozilla Firefox will NOT work) for the IDE to function correctly. Here are the steps to follow:

1.Download and install Eclipse 3.02.

2.Download and install Mozilla 1.6

3.Once Mozilla 1.6 is installed:

check if the shell variable MOZILLA_FIVE_HOME is set and points to Mozilla 1.6.

$ echo $MOZILLA_FIVE_HOME
If necessary, set correctly by doing:

$ MOZILLA_FIVE_HOME=<Mozilla 1.6 install directory>
$ export MOZILLA_FIVE_HOME

4.Startup eclipse by doing the following;
$ cd <Eclipse 3.02 install directory>
$ ./eclipse -vmargs -Dorg.eclipse.swt.browser.internal.flash

(This will enable the Flash Player in the SWT Browser)

6.Put eclipse to your required directory i.e home/username/myprograms/eclipse

7.Test Eclipse, to make sure its functioning then close the application.

8.Extract the laszloIDE.zip file, rename folder to “lasloIDE”

9.Open Eclipse, From the Eclipse menu, click "Help -> Software Updates -> Find and Install...". Select "Search for new features to install".

10. Create a "New Archived Site..." pointer to the downloaded folder we created in step8.

11. Click the checkbox next to the new "laszloIDE.zip" site pointer to select all four site components, then click "Next". You may get a "Integrity Personal Policy Alert" message from Windows warning about executing java. If so, then accept this message.

12. Click "Select All" to select all five features, then click "Next".

13. Persue the licenses, click "I accept the terms in the license agreements", then click "Next".

14. Each feature is downloaded. Click "Install" for each feature (five times). Be patient, as the Eclipse download server can be slow at certain times.

15. Restart Eclipse as the last step. (By clicking "Yes").

16. Extract the lazslo server file “openlaszlo-3.0-unix.tar.gz”

17.Add the directory lps-3.0 to your required location.

18. Run the server in bash, change directory i.e
/home/username/myprograms/lps-3.0/Server/tomcat-5.0.24/bin

19. In Bash type ./startup.sh

20. Your server should now be running.

21. Repeat step 3 if necessary.

22. Startup eclipse by doing the following;

$ cd <Eclipse 3.02 install directory>
$ ./eclipse -vmargs -Dorg.eclipse.swt.browser.internal.flash

23. In eclipse environment goto Window>Preferences and select Laszlo at the left hand side.

24.For LPS Web Root set it to ....../lps-3.0/Server/lps-3.0 you can use browse for this.

25. You should notice the “context root” has now changed to lps-3.0.

26.For web browser location you need to point it to the mozilla 1.6 which was installed earlier. In my case this is /usr/local/mozilla/mozilla

27.Click Apply

28. Goto Window>Customize Perspective and check the Laszlo and click ok.

29.Note:The Laszlo Presentation Server must be running in order for the design view to work.

30.From the Eclipse menu, click "File -> New -> Project...". Select "Laszlo -> Laszlo Project".

31.You may also be prompted to switch to the Laszlo perspective, and you should do so.

32.The first time you create a Laszlo project, you will be prompted for the location of the Laszlo Presentation Server.

33.Expand your newly created Laszlo Project in the left-hand Navigator window. Select the src folder. Right-click on the src folder and click "New -> Laszlo File". Click "Finish".

34.Drag and drop a component (such as button) from the right-hand Palette window into the <canvas> tag. Then, type a string such as "Hello World!" inside your new tag (for example, <canvas><button>Hello World!</button></canvas>)

35.Try using xml code assist (ctrl+space) for xml elements and attributes.

36. Switch to the design tab and see what it looks like.

37. Click on the component, and drag on the corners of the item to resize it, or drag on the top middel to move the component.

38. Save your Laszlo file.

39. From the Eclipse menu, click "Run -> Run...". Select "Laszlo Application" and "New". Select your project, and enter a file path (i.e. /src/new_file.lzx)

40. You should see your test file when you click "Run".

You may want to consider setting MOZILLA_FIVE_HOME permanently
to do this add the following code to the end of the file:

$ /home/username/.bashrc

MOZILLA_FIVE_HOME=/your/mozilla/directory
export MOZILLA_FIVE_HOME

And there you have it, mine works as it should. Hope this works for you...[/QUOTE]

---

### Post by Michael on 2005-06-03
Can you please describe, in short, what is Laszlo?

---

### Post by bored2k on 2005-06-03
[QUOTE=Michael]Can you please describe, in short, what is Laszlo?[/QUOTE]
 > IDE for Laszlo is a technology preview of an Eclipse-based development environment for creating, editing, debugging, and testing applications based on the LZX (an XML and JavaScript description language).Version 2.0 provides a visual (wysiwyg) editor, support for the latest OpenLaszlo 3.0, user interface improvements, and miscellaneous bug fixes. .

---


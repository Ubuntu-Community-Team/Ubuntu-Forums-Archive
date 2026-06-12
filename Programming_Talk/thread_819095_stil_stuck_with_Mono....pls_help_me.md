---
title: "stil stuck with Mono....pls help me"
date: 2008-06-05
forum: Programming Talk
---

### Post by x88a on 2008-06-05
i am trying to run a file called "Program.cs" using Mono.

Here is the Program.cs content:-

&#65279;using System;

using System.Collections.Generic;

using System.Windows.Forms;



namespace ECamTools {

static class Program {

/// <summary>

/// Der Haupteinstiegspunkt für die Anwendung.

/// </summary>

[STAThread]

static void Main(string[] args) {

Application.EnableVisualStyles();

Application.SetCompatibleTextRenderingDefault(fals e);

Application.Run(new ECamViewer(args));

}

}

}



after typing "gmcs Program.cs", i get this error:-

Program.cs(3,14): error CS0234: The type or namespace name `Windows' does not exist in the namespace `System'. Are you missing an assembly reference?
Program.cs(3,1): error CS0246: The type or namespace name `Windows.Forms' could not be found. Are you missing a using directive or an assembly reference?
Compilation failed: 2 error(s), 0 warnings


After referring this this webpage: [http://ubuntuforums.org/showthread.php?t=722869](http://ubuntuforums.org/showthread.php?t=722869) , i managed to cut my error from 4 to 2.
i am using Mono JIT compiler version 1.2.3.1.
From my intepretation, the errors are all based on the libraries.
What is wrong?

Pls help.

TQ

---

### Post by LaRoza on 2008-06-05
Double post, for best help, keep everything together for one issue.

---


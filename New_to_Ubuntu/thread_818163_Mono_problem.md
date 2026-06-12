---
title: "Mono problem"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by x88a on 2008-06-04
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

            Application.SetCompatibleTextRenderingDefault(false);

            Application.Run(new ECamViewer(args));

        }

    }

}



after typing "mcs Program.cs", i get this error:-

Program.cs(2,7): error CS0234: The type or namespace name `Generic' does not exist in the namespace `System.Collections'. Are you missing an assembly reference?
Program.cs(2,1): error CS0246: The type or namespace name `Collections.Generic' could not be found. Are you missing a using directive or an assembly reference?
Program.cs(3,7): error CS0234: The type or namespace name `Windows' does not exist in the namespace `System'. Are you missing an assembly reference?
Program.cs(3,1): error CS0246: The type or namespace name `Windows.Forms' could not be found. Are you missing a using directive or an assembly reference?
Compilation failed: 4 error(s), 0 warnings


From my intepretation, the errors are all based on the libraries.
What is wrong?

Pls help.

TQ

---

### Post by Vadi on 2008-06-04
I think you'd get better support if you posted it in the programming forum ([click]("http://ubuntuforums.org/forumdisplay.php?f=39")). Does look like it's missing some libraries - maybe mono has them named differently or something.

---


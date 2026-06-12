---
title: "File Default.aspx.${language Extension} could not  be written"
date: 2010-03-29
forum: Programming Talk
---

### Post by halit.yilmaz on 2010-03-29
Hi,

I've installed MonoDevelop 2.2. When I want to create web applications ( ASP.NET) it gives "File Default.aspx.${language Extension} could not  be written" error. When i want to add a new file with codebehind i have errors as well.

here is a code group( i wanted to see the errors from terminal)
> 
halit@halit-laptop:~$ monodevelop
WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.
UYARI [2010-03-29 11:08:27Z]: GLib-Warning: g_set_prgname() called multiple times
Stack trace: 
   at GLib.Global.set_ProgramName(System.String value)
   at Gtk.Application.SetPrgname()
   at Gtk.Application.do_init(System.String progname, System.String[] ByRef args, Boolean check)
   at Gtk.Application.Init(System.String progname, System.String[] ByRef args)
   at MonoDevelop.Ide.Gui.IdeStartup.Run(System.String[] args)
   at MonoDevelop.Startup.MonoDevelopMain.Main(System.String[] args)
UYARI [2010-03-29 11:08:32Z]: Inotify watch limit is too low (8192).
MonoDevelop will switch to managed file watching.
See [http://monodevelop.com/Inotify_Watches_Limit](http://monodevelop.com/Inotify_Watches_Limit) for more info.
HATA [2010-03-29 11:09:35Z]: Unparseable template: 'using System;
using System.Web;
using System.Web.UI;

namespace hastane {
    
    public partial class ${EscapedIdentifier} : System.Web.UI.Page
    {
        
    }
}'.
System.ArgumentException: -- line 7 col 24: invalid Identifier

  at MonoDevelop.CSharp.CSharpEnhancedCodeProvider.ParseInternal (System.IO.TextReader codeStream) [0x00000] 
  at MonoDevelop.CSharp.CSharpEnhancedCodeProvider.Parse (System.IO.TextReader codeStream) [0x00000] 
  at MonoDevelop.Ide.Templates.CodeTranslationFileDescriptionTemplate.CreateContent (MonoDevelop.Projects.Project project, System.Collections.Generic.Dictionary`2 tags, System.String language) [0x00000] 
halit@halit-laptop:~$ clear

halit@halit-laptop:~$ monodevelop
WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.
UYARI [2010-03-29 11:10:31Z]: GLib-Warning: g_set_prgname() called multiple times
Stack trace: 
   at GLib.Global.set_ProgramName(System.String value)
   at Gtk.Application.SetPrgname()
   at Gtk.Application.do_init(System.String progname, System.String[] ByRef args, Boolean check)
   at Gtk.Application.Init(System.String progname, System.String[] ByRef args)
   at MonoDevelop.Ide.Gui.IdeStartup.Run(System.String[] args)
   at MonoDevelop.Startup.MonoDevelopMain.Main(System.String[] args)
UYARI [2010-03-29 11:10:32Z]: Inotify watch limit is too low (8192).
MonoDevelop will switch to managed file watching.
See [http://monodevelop.com/Inotify_Watches_Limit](http://monodevelop.com/Inotify_Watches_Limit) for more info.
HATA [2010-03-29 11:11:00Z]: Unparseable template: 'using System;
using System.Web;
using System.Web.UI;

namespace test {
    
    public partial class ${EscapedIdentifier} : System.Web.UI.Page
    {
        public void button1Clicked (object sender, EventArgs args)
        {
            button1.Text = "You clicked me";
        }
    }
}'.
System.ArgumentException: -- line 7 col 24: invalid Identifier

  at MonoDevelop.CSharp.CSharpEnhancedCodeProvider.ParseInternal (System.IO.TextReader codeStream) [0x00000] 
  at MonoDevelop.CSharp.CSharpEnhancedCodeProvider.Parse (System.IO.TextReader codeStream) [0x00000] 
  at MonoDevelop.Ide.Templates.CodeTranslationFileDescriptionTemplate.CreateContent (MonoDevelop.Projects.Project project, System.Collections.Generic.Dictionary`2 tags, System.String language) [0x00000] 
HATA [2010-03-29 11:11:05Z]: Dosya Default.aspx.${LanguageExtension} yaz&#305;lamad&#305;.
System.ArgumentException: -- line 7 col 24: invalid Identifier

  at MonoDevelop.CSharp.CSharpEnhancedCodeProvider.ParseInternal (System.IO.TextReader codeStream) [0x00000] 
  at MonoDevelop.CSharp.CSharpEnhancedCodeProvider.Parse (System.IO.TextReader codeStream) [0x00000] 
  at MonoDevelop.Ide.Templates.CodeTranslationFileDescriptionTemplate.CreateContent (MonoDevelop.Projects.Project project, System.Collections.Generic.Dictionary`2 tags, System.String language) [0x00000] 
HATA [2010-03-29 11:11:05Z]: Unparseable template: 'using System;
using System.Web;
using System.Web.UI;

namespace test {
    
    public partial class ${EscapedIdentifier}
    {
        protected System.Web.UI.WebControls.Button button1;
    }
}'.
System.ArgumentException: -- line 7 col 24: invalid Identifier

  at MonoDevelop.CSharp.CSharpEnhancedCodeProvider.ParseInternal (System.IO.TextReader codeStream) [0x00000] 
  at MonoDevelop.CSharp.CSharpEnhancedCodeProvider.Parse (System.IO.TextReader codeStream) [0x00000] 
  at MonoDevelop.Ide.Templates.CodeTranslationFileDescriptionTemplate.CreateContent (MonoDevelop.Projects.Project project, System.Collections.Generic.Dictionary`2 tags, System.String language) [0x00000] 
HATA [2010-03-29 11:11:06Z]: Dosya Default.aspx.designer.${LanguageExtension} yaz&#305;lamad&#305;.
System.ArgumentException: -- line 7 col 24: invalid Identifier

  at MonoDevelop.CSharp.CSharpEnhancedCodeProvider.ParseInternal (System.IO.TextReader codeStream) [0x00000] 
  at MonoDevelop.CSharp.CSharpEnhancedCodeProvider.Parse (System.IO.TextReader codeStream) [0x00000] 
  at MonoDevelop.Ide.Templates.CodeTranslationFileDescriptionTemplate.CreateContent (MonoDevelop.Projects.Project project, System.Collections.Generic.Dictionary`2 tags, System.String language) [0x00000] 
HATA [2010-03-29 11:11:56Z]: Unparseable template: 'using System;
using System.Web;
using System.Web.UI;

namespace test {
    
    public partial class ${EscapedIdentifier} : System.Web.UI.Page
    {
        
    }
}'.
System.ArgumentException: -- line 7 col 24: invalid Identifier

  at MonoDevelop.CSharp.CSharpEnhancedCodeProvider.ParseInternal (System.IO.TextReader codeStream) [0x00000] 
  at MonoDevelop.CSharp.CSharpEnhancedCodeProvider.Parse (System.IO.TextReader codeStream) [0x00000] 
  at MonoDevelop.Ide.Templates.CodeTranslationFileDescriptionTemplate.CreateContent (MonoDevelop.Projects.Project project, System.Collections.Generic.Dictionary`2 tags, System.String language) [0x00000] 


what can i do to solve this problem?

Thank you.

---


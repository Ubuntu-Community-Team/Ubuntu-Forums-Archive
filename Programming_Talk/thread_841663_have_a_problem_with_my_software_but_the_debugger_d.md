---
title: "have a problem with my software but the debugger doesn't show it"
date: 2008-06-26
forum: Programming Talk
---

### Post by dinbrca on 2008-06-26
when i try to run the software the software gets to 50% compiled but never start... it shows no error, warrnings or messages.. although when i quit from Monodevelop it shows two error messages.. those are the errors:
1)
Unhandled Exception. (let me clicks a button that shows details and that shows):
```

Exception occurred: XSLT compile error. Named template GtkTable_fixoptions is already registered..

System.Xml.Xsl.XsltCompileException: XSLT compile error. Named template GtkTable_fixoptions is already registered.. ---> System.InvalidOperationException: Named template GtkTable_fixoptions is already registered.
  at Mono.Xml.Xsl.XslTemplateTable.Add (Mono.Xml.Xsl.XslTemplate template) [0x00000] 
  at Mono.Xml.Xsl.XslStylesheet.HandleTopLevelElement (Mono.Xml.Xsl.Compiler c) [0x00000] 
  at Mono.Xml.Xsl.XslStylesheet.ProcessTopLevelElements (Mono.Xml.Xsl.Compiler c) [0x00000] 
  at Mono.Xml.Xsl.XslStylesheet.Compile (Mono.Xml.Xsl.Compiler c) [0x00000] 
  at Mono.Xml.Xsl.Compiler.Compile (System.Xml.XPath.XPathNavigator nav, System.Xml.XmlResolver res, System.Security.Policy.Evidence evidence) [0x00000] --- End of inner exception stack trace ---

  at Mono.Xml.Xsl.Compiler.Compile (System.Xml.XPath.XPathNavigator nav, System.Xml.XmlResolver res, System.Security.Policy.Evidence evidence) [0x00000] 
  at System.Xml.Xsl.XslTransform.Load (System.Xml.XPath.XPathNavigator stylesheet, System.Xml.XmlResolver resolver, System.Security.Policy.Evidence evidence) [0x00000] 
  at System.Xml.Xsl.XslTransform.Load (IXPathNavigable stylesheet, System.Xml.XmlResolver resolver, System.Security.Policy.Evidence evidence) [0x00000] 
  at Stetic.Registry.UpdateGladeTransform () [0x00000] 
  at Stetic.Registry.InternalUpdate () [0x00000] 
  at Stetic.Registry.UnregisterWidgetLibrary (Stetic.WidgetLibrary library) [0x00000] 
  at Stetic.ApplicationBackend.UpdateLibraries (System.Collections.ArrayList libraries, System.Collections.ArrayList projects, Boolean allowBackendRestart, Boolean forceUnload) [0x00000] 
  at (wrapper remoting-invoke-with-check) Stetic.ApplicationBackend:UpdateLibraries (System.Collections.ArrayList,System.Collections.ArrayList,bool,bool)
  at Stetic.Application.UpdateWidgetLibraries (Boolean allowBackendRestart, Boolean forceUnload) [0x00000] 
  at (wrapper remoting-invoke-with-check) Stetic.Application:UpdateWidgetLibraries (bool,bool)
  at Stetic.Project.Dispose () [0x00000] 
  at (wrapper remoting-invoke-with-check) Stetic.Project:Dispose ()
  at MonoDevelop.GtkCore.GuiBuilder.GuiBuilderProject.Unload () [0x00000] 
  at MonoDevelop.GtkCore.GuiBuilder.GuiBuilderProject.Dispose () [0x00000] 
  at MonoDevelop.GtkCore.GtkDesignInfo.Dispose () [0x00000] 
  at MonoDevelop.Projects.CombineEntry.Dispose () [0x00000] 
  at MonoDevelop.Projects.Project.Dispose () [0x00000] 
  at MonoDevelop.Projects.Combine.Dispose () [0x00000] 
  at MonoDevelop.Ide.Gui.ProjectOperations.CloseCombine (Boolean saveCombinePreferencies) [0x00000] 
  at MonoDevelop.Ide.Gui.DefaultWorkbench.Close () [0x00000] 
  at MonoDevelop.Ide.Gui.DefaultWorkbench.OnClosing (System.Object o, Gtk.DeleteEventArgs e) [0x00000] 
  at Gtk.Widget.DeleteEventSignalCallback (IntPtr arg0, IntPtr arg1, IntPtr gch) [0x00000] 

```

2)
Unhandled Exception. (let me clicks a button that shows details and that shows):
```

Exception occurred: List has changed.

System.InvalidOperationException: List has changed.
  at System.Collections.ArrayList+SimpleEnumerator.MoveNext () [0x00000] 
  at MonoDevelop.Components.DockToolbars.FixedPanel.ForAll (Boolean include_internals, Gtk.Callback callback) [0x00000] 
  at Gtk.Container.Forall_cb (IntPtr container, Boolean include_internals, IntPtr cb, IntPtr data) [0x00000] 

```

and then it quits from mono..
thx for the helpers..

---


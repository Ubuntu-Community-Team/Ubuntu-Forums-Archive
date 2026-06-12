---
title: "errors trying to compile monodevelop 2.2"
date: 2009-12-17
forum: Packaging and Compiling Programs
---

### Post by deltazed on 2009-12-17
Its a really long story,  including a successful build of the lastest stable version of mono into /opt/mono_stable.   I know this stuff is really new...  but I'm hoping someone can clue me on on the best way to resolve the errors  when I try and make monodevelop-2.2
....

Making all in MonoDevelop.Projects.Formats.MSBuild
make[3]: Entering directory `/home/dz/monodev/monodevpackages/monodevelop-2.2/src/core/MonoDevelop.Projects.Formats.MSBuild'
/usr/bin/gmcs -debug -codepage:utf8 -warnaserror -debug -out:../../../build/bin/MonoDevelop.Projects.Formats.MSBuild.exe -target:winexe -r:Microsoft.Build.Engine -r:Microsoft.Build.Framework -r:Microsoft.Build.Utilities -r:System -r:System.Runtime.Remoting   ./AssemblyInfo.cs ./Main.cs ./MonoDevelop.Projects.Formats.MSBuild/ILogWriter.cs ./MonoDevelop.Projects.Formats.MSBuild/IProjectBuilder.cs ./MonoDevelop.Projects.Formats.MSBuild/LocalLogger.cs ./MonoDevelop.Projects.Formats.MSBuild/MSBuildResult.cs ./MonoDevelop.Projects.Formats.MSBuild/ProjectBuilder.cs 
error CS0006: cannot find metadata file `Microsoft.Build.Engine'
error CS0006: cannot find metadata file `Microsoft.Build.Framework'
error CS0006: cannot find metadata file `Microsoft.Build.Utilities'
Compilation failed: 3 error(s), 0 warnings

---

### Post by Yellow Pasque on 2009-12-17
Make sure you have all of the dependencies?:
```
sudo apt-get build-dep monodevelop
```

---

### Post by chosenperfect on 2010-01-18
hi, i have the same problem, but not indeed the same ^^

i have install most of the build dep:
```

sudo aptitude install \
libgnomeui-dev \
libgnomecanvas2-dev \
libgnomeprint2.2-dev \
libgnomeprintui2.2-dev \
libpanel-applet2-dev \
libgnome2-dev \
libgnome2-doc \
libgnomeprint2.2-doc \
libgnomeui-doc \
libpango1.0-dev \
libatk1.0-dev \
libgtk2.0-dev \
libglade2-dev \
libncurses5-dev \
build-essential \
pkg-config \
libglib2.0-dev \
bison \
libcairo2-dev \
libungif4-dev \
libjpeg62-dev \
libtiff4-dev \
gettext \
libgnome-desktop-dev \

```

my install script
```

var='libgdiplus mono mcs gtk-sharp gnome-sharp gnome-desktop-sharp mono-tools mono-addins webkit-sharp xsp monodevelop'

for x in $var; do echo $x; svn co svn://anonsvn.mono-project.com/source/trunk/$x ; done;

source ./mono-environment
idir=/opt/mono
#sudo mkdir $idir
sudo chown kyz:kyz $idir
mono -V

cd libgdiplus
        ./autogen.sh --prefix=$idir
        make
        sudo make install
cd ..

cd mono
        ./autogen.sh --prefix=$idir
        make
        sudo make install
cd ..

cd gtk-sharp
        ./bootstrap-for-the-insane --prefix=$idir
        make
        sudo make install
cd ..

cd gnome-sharp
        ./bootstrap-2.24 --prefix=$idir
        make
        sudo make install
cd ..

var2='webkit-sharp gnome-desktop-sharp mono-tools mono-addins xsp'

for x in $var2; do
        cd $x
        ./autogen.sh --prefix=$idir
        make
        sudo make install
        cd ..
done;

cd monodevelop
        ./configure --prefix=$idir
        make
        sudo make install
cd ..

```the build process mostly success, except mono-tools and monodevelop, that is:

the error when making mono-tools:
```

make[1]: Entering directory `/media/a5-128/monodevelop/mono-tools/gui-compare'
/opt/mono/bin/gmcs -noconfig -codepage:utf8 -warn:4 -optimize+ -debug -define:DEBUG -target:exe -out:gui-compare.exe ./gtk-gui/generated.cs ./MainWindow.cs ./gtk-gui/MainWindow.cs ./Main.cs ./AssemblyInfo.cs ./InfoManager.cs ./CompareContext.cs ./Comparison.cs ./Metadata.cs ./MasterMetadata.cs ./Masterinfo.cs ./CecilMetadata.cs ./ProviderSelector.cs ./gtk-gui/guicompare.ProviderSelector.cs ./AssemblyResolver.cs ./Config.cs ./CustomCompare.cs ./gtk-gui/GuiCompare.CustomCompare.cs  -resource:./gtk-gui/gui.stetic,gui.stetic  -resource:./cm/c.gif,c.gif  -resource:./cm/d.gif,d.gif  -resource:./cm/e.gif,e.gif  -resource:./cm/en.gif,en.gif  -resource:./cm/f.gif,f.gif  -resource:./cm/i.gif,i.gif  -resource:./cm/m.gif,m.gif  -resource:./cm/n.gif,n.gif  -resource:./cm/p.gif,p.gif  -resource:./cm/r.gif,r.gif  -resource:./cm/s.gif,s.gif  -resource:./cm/sc.gif,sc.gif  -resource:./cm/se.gif,se.gif  -resource:./cm/sm.gif,sm.gif  -resource:./cm/st.gif,st.gif  -resource:./cm/sx.gif,sx.gif  -resource:./cm/tb.gif,tb.gif  -resource:./cm/tm.gif,tm.gif  -resource:./cm/tp.gif,tp.gif  -resource:./cm/w.gif,w.gif  -resource:./cm/y.gif,y.gif  -resource:./gtk-gui/objects.xml,objects.xml  -resource:./cm/mn.png,mn.png -pkg:gtk-sharp-2.0 -pkg:glib-sharp-2.0 -pkg:glade-sharp-2.0 -r:/opt/mono/lib/mono/gac/Mono.Cecil/0.6.9.0__0738eb9f132ed756/Mono.Cecil.dll -r:System -r:System.Core -r:Mono.Posix -r:System.Xml
./gtk-gui/MainWindow.cs(21,24): error CS0102: The type `MainWindow' already contains a definition for `Compare'
./MainWindow.cs(577,21): (Location of the symbol related to previous error)
Compilation failed: 1 error(s), 0 warnings
make[1]: *** [gui-compare.exe] Error 1
make[1]: Leaving directory `/media/a5-128/monodevelop/mono-tools/gui-compare'
make: *** [all-recursive] Error 1

```the error when making monodevelop:

```

make[4]: Entering directory `/media/a5-128/monodevelop/monodevelop/main/src/core/MonoDevelop.Projects.Gui'
/opt/mono/bin/gmcs -debug -codepage:utf8 -out:../../../build/bin/MonoDevelop.Projects.Gui.dll -target:library -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll   -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll   -r:/opt/mono/lib/mono/mono-addins/Mono.Addins.dll   -r:Mono.Posix -r:System -r:System.Core -r:System.Xml -r:../../../build/bin/MonoDevelop.Components.dll -r:../../../build/bin/MonoDevelop.Core.dll -r:../../../build/bin/MonoDevelop.Core.Gui.dll -r:../../../build/bin/MonoDevelop.Projects.dll /resource:./gtk-gui/gui.stetic /resource:./gtk-gui/objects.xml /resource:./MonoDevelop.Projects.Gui.addin.xml ./AssemblyInfo.cs ./gtk-gui/generated.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.AddMimeTypeDialog.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.DeleteConfigDialog.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.NewConfigurationDialog.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.OptionPanels.BaseDirectoryPanelWidget.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.OptionPanels.CodeFormattingPanelWidget.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.OptionPanels.CombineBuildOptionsWidget.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.OptionPanels.CombineConfigurationPanelWidget.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.OptionPanels.CombineEntryConfigurationsPanelWidget.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.OptionPanels.CombineInformationWidget.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.OptionPanels.CommonAssemblySigningPreferences.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.OptionPanels.CustomCommandPanelWidget.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.OptionPanels.CustomCommandWidget.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.OptionPanels.GeneralProjectOptionsWidget.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.OptionPanels.NamespaceSynchronisationPanelWidget.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.OptionPanels.OutputOptionsPanelWidget.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.OptionPanels.RunOptionsPanelWidget.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.OptionPanels.RuntimeOptionsPanelWidget.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.OptionPanels.StartupOptionsPanelWidget.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.ProjectFileSelectorDialog.cs ./gtk-gui/MonoDevelop.Projects.Gui.Dialogs.RenameConfigDialog.cs ./MonoDevelop.Projects.Gui.Completion/CodeCompletionContext.cs ./MonoDevelop.Projects.Gui.Completion/CompletionData.cs ./MonoDevelop.Projects.Gui.Completion/CompletionDataList.cs ./MonoDevelop.Projects.Gui.Completion/CompletionListWindow.cs ./MonoDevelop.Projects.Gui.Completion/CompletionWindowManager.cs ./MonoDevelop.Projects.Gui.Completion/DeclarationViewWindow.cs ./MonoDevelop.Projects.Gui.Completion/ICompletionData.cs ./MonoDevelop.Projects.Gui.Completion/ICompletionWidget.cs ./MonoDevelop.Projects.Gui.Completion/IMemberCompletionData.cs ./MonoDevelop.Projects.Gui.Completion/IParameterDataProvider.cs ./MonoDevelop.Projects.Gui.Completion/ListWidget.cs ./MonoDevelop.Projects.Gui.Completion/ListWindow.cs ./MonoDevelop.Projects.Gui.Completion/MutableCompletionDataList.cs ./MonoDevelop.Projects.Gui.Completion/ParameterInformationWindow.cs ./MonoDevelop.Projects.Gui.Completion/ParameterInformationWindowManager.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/ActiveLanguageCondition.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/BaseDirectoryPanel.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/BaseDirectoryPanelWidget.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/CodeFormattingPanel.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/CombineBuildOptions.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/CombineConfigurationPanel.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/CombineInformationPanel.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/CommonAssemblySigningPreferences.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/CustomCommandPanel.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/CustomCommandPanelWidget.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/CustomCommandWidget.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/EnvVarList.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/GeneralProjectOptions.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/NamespaceSynchronisationPanel.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/OutputOptionsPanel.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/RunOptionsPanel.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/RuntimeOptionsPanel.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/SolutionItemConfigurationsPanel.cs ./MonoDevelop.Projects.Gui.Dialogs.OptionPanels/StartupOptionsPanel.cs ./MonoDevelop.Projects.Gui.Dialogs/AddMimeTypeDialog.cs ./MonoDevelop.Projects.Gui.Dialogs/CombineOptionsDialog.cs ./MonoDevelop.Projects.Gui.Dialogs/DefaultPolicyOptionsDialog.cs ./MonoDevelop.Projects.Gui.Dialogs/DeleteConfigDialog.cs ./MonoDevelop.Projects.Gui.Dialogs/ItemOptionsDialog.cs ./MonoDevelop.Projects.Gui.Dialogs/ItemOptionsPanel.cs ./MonoDevelop.Projects.Gui.Dialogs/MimeTypePolicyOptionsPanel.cs ./MonoDevelop.Projects.Gui.Dialogs/MimeTypePolicyOptionsSection.cs ./MonoDevelop.Projects.Gui.Dialogs/MultiConfigItemOptionsDialog.cs ./MonoDevelop.Projects.Gui.Dialogs/MultiConfigItemOptionsPanel.cs ./MonoDevelop.Projects.Gui.Dialogs/NewConfigurationDialog.cs ./MonoDevelop.Projects.Gui.Dialogs/PolicyOptionsPanel.cs ./MonoDevelop.Projects.Gui.Dialogs/ProjectFileSelectorDialog.cs ./MonoDevelop.Projects.Gui.Dialogs/ProjectOptionsDialog.cs ./MonoDevelop.Projects.Gui.Dialogs/RenameConfigDialog.cs ./MonoDevelop.Projects.Gui.Extensions/MimeTypeOptionsPanelNode.cs ./MonoDevelop.Projects.Gui/ProjectFileEntry.cs ./MonoDevelop.Projects.Gui/ProjectsGuiServices.cs

** (/opt/mono/lib/mono/2.0/gmcs.exe:12131): WARNING **: The following assembly referenced from /media/a5-128/monodevelop/monodevelop/main/build/bin/MonoDevelop.Components.dll could not be loaded:
     Assembly:   glade-sharp    (assemblyref_index=12)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/media/a5-128/monodevelop/monodevelop/main/build/bin/).


** (/opt/mono/lib/mono/2.0/gmcs.exe:12131): WARNING **: Could not load file or assembly 'glade-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.Reflection.ReflectionTypeLoadException: The classes in the module cannot be loaded.
  at (wrapper managed-to-native) System.Reflection.Assembly:GetTypes (System.Reflection.Assembly*,bool)
  at System.Reflection.Assembly.GetTypes () [0x00000] in <filename unknown>:0
  at Mono.CSharp.RootNamespace.ComputeNamespaces (System.Reflection.Assembly assembly, System.Type extensionType) [0x00000] in <filename unknown>:0
  at Mono.CSharp.RootNamespace.ComputeNamespace (Mono.CSharp.CompilerContext ctx, System.Type extensionType) [0x00000] in <filename unknown>:0
  at Mono.CSharp.GlobalRootNamespace.ComputeNamespaces (Mono.CSharp.CompilerContext ctx) [0x00000] in <filename unknown>:0
  at Mono.CSharp.Driver.LoadReferences () [0x00000] in <filename unknown>:0
  at Mono.CSharp.Driver.Compile () [0x00000] in <filename unknown>:0
  at Mono.CSharp.Driver.Main (System.String[] args) [0x00000] in <filename unknown>:0
make[4]: *** [../../../build/bin/MonoDevelop.Projects.Gui.dll] Error 1
make[4]: Leaving directory `/media/a5-128/monodevelop/monodevelop/main/src/core/MonoDevelop.Projects.Gui'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/media/a5-128/monodevelop/monodevelop/main/src/core'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/media/a5-128/monodevelop/monodevelop/main/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/a5-128/monodevelop/monodevelop/main'
make: *** [all-recursive] Error 1

```

could anyone help ^^ thanks

---


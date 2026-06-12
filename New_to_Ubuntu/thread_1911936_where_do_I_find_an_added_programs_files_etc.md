---
title: "where do I find an added programs files etc?"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by cliveT on 2012-01-19
I have recently added a CAD (QCAD) program and in order to add a "Block" that I have drawn I need look up the folder where QCAD is installed to and open it then find a folder inside called Library then add another folder of my choice -

Where do I find/open the installation folder of QCAD, I downloaded QCAD as a bin file to my desktop and installed it ok, but where is the files and programs folders kept?

Regards

Clive

---

### Post by MG&amp;TL on 2012-01-19
Run:

```
sudo updatedb
locate QCAD
```

and post output.

---

### Post by cliveT on 2012-01-19
that doesn`t work!

---

### Post by cliveT on 2012-01-19
This is what I get -


clive@clive-Inspiron-N5110:~$ sudo updatedb
[sudo] password for clive: 
Sorry, try again.
[sudo] password for clive: 
clive@clive-Inspiron-N5110:~$ sudo updatedb
clive@clive-Inspiron-N5110:~$ locate QCAD
/home/clive/.config/RibbonSoft/QCAD3.conf
/home/clive/.config/RibbonSoft/QCADLibraryBrowser.conf
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Preferences/Shortcuts/Schemas/QCAD.kms
clive@clive-Inspiron-N5110:~$

---

### Post by MG&amp;TL on 2012-01-19
> **cliveT said:**
> that doesn`t work!

...bit more detail please?

Open a (Ctrl-Alt-T) terminal, then type those commands in.

---

### Post by MG&amp;TL on 2012-01-19
> **cliveT said:**
> This is what I get -


clive@clive-Inspiron-N5110:~$ sudo updatedb
[sudo] password for clive: 
Sorry, try again.
[sudo] password for clive: 
clive@clive-Inspiron-N5110:~$ sudo updatedb
clive@clive-Inspiron-N5110:~$ locate QCAD
/home/clive/.config/RibbonSoft/QCAD3.conf
/home/clive/.config/RibbonSoft/QCADLibraryBrowser.conf
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Preferences/Shortcuts/Schemas/QCAD.kms
clive@clive-Inspiron-N5110:~$


Okay, that's a little weird.

UNIX is case-sensitive, so try 'qcad', 'Qcad' etc.

---

### Post by ajgreeny on 2012-01-19
Try ```
locate -i qcad
```instead of QCAD, which will ignore the letter case.

How did you install qcad; was it from a .deb file, or from source that you compiled,  or a tar.gz or similar?

Too slow, again.

---

### Post by MG&amp;TL on 2012-01-19
> **ajgreeny said:**
> Try ```
locate -i qcad
```instead of QCAD, which will ignore the letter case.

How did you install qcad; was it from a .deb file, or from source that you compiled,  or a tar.gz or similar?

Thanks for the locate option; I need to read manpages more often!

The OP said a .bin file.

---

### Post by cliveT on 2012-01-19
From website download area -bin file, I`m now going to try 
locate -i qcad

---

### Post by cliveT on 2012-01-19
> **cliveT said:**
> From website download area -bin file, I`m now going to try 
locate -i qcad

OK that gave me a bit more - any ideas!

```
pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/HelpViewer/HelpViewer.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/HelpViewer/Next.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/HelpViewer/Previous.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/HelpViewer/Printer.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/HelpViewer/Reload.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/HelpViewer/Stop.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/HelpViewer/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/HelpViewer/ts/HelpViewer_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/HelpViewer/ts/HelpViewer_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/HelpViewer/ts/HelpViewer_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/HelpViewer/ts/HelpViewer_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/HelpViewer/ts/HelpViewer_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/HelpViewer/ts/HelpViewer_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/HelpViewer/ts/HelpViewer_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/HelpViewer/ts/HelpViewer_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/LayerList.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/LayerList.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/LayerList.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/layerstatus_00.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/layerstatus_01.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/layerstatus_10.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/layerstatus_11.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/ts/LayerList.pt.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/ts/LayerList.pt_BR.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/ts/LayerList_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/ts/LayerList_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/ts/LayerList_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/ts/LayerList_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/ts/LayerList_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/ts/LayerList_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/ts/LayerList_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/LayerList/ts/LayerList_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/MouseDisplay/Mouse.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/MouseDisplay/MouseDisplay.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/MouseDisplay/MouseDisplay.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/MouseDisplay/MouseDisplay.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/MouseDisplay/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/MouseDisplay/ts/MouseDisplay_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/MouseDisplay/ts/MouseDisplay_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/MouseDisplay/ts/MouseDisplay_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/MouseDisplay/ts/MouseDisplay_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/MouseDisplay/ts/MouseDisplay_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/MouseDisplay/ts/MouseDisplay_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/MouseDisplay/ts/MouseDisplay_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/MouseDisplay/ts/MouseDisplay_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/OptionsToolBar/OptionsToolBar.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/OptionsToolBar/OptionsToolBar.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/OptionsToolBar/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/OptionsToolBar/ts/OptionsToolBar.pt.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/OptionsToolBar/ts/OptionsToolBar.pt_BR.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/OptionsToolBar/ts/OptionsToolBar_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/OptionsToolBar/ts/OptionsToolBar_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/OptionsToolBar/ts/OptionsToolBar_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/OptionsToolBar/ts/OptionsToolBar_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/OptionsToolBar/ts/OptionsToolBar_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/OptionsToolBar/ts/OptionsToolBar_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/OptionsToolBar/ts/OptionsToolBar_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/OptionsToolBar/ts/OptionsToolBar_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PenToolBar/PenToolBar.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PenToolBar/PenToolBar.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PenToolBar/PenToolBar.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PenToolBar/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PenToolBar/ts/PenToolBar_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PenToolBar/ts/PenToolBar_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PenToolBar/ts/PenToolBar_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PenToolBar/ts/PenToolBar_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PenToolBar/ts/PenToolBar_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PenToolBar/ts/PenToolBar_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PenToolBar/ts/PenToolBar_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PenToolBar/ts/PenToolBar_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ProgressBar/Close.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ProgressBar/ProgressBar.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ProgressBar/ProgressBar.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ProgressBar/ProgressBar.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ProgressBar/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ProgressBar/ts/ProgressBar_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ProgressBar/ts/ProgressBar_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ProgressBar/ts/ProgressBar_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ProgressBar/ts/ProgressBar_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ProgressBar/ts/ProgressBar_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ProgressBar/ts/ProgressBar_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ProgressBar/ts/ProgressBar_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ProgressBar/ts/ProgressBar_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/AddCustomProperty.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/AddLayer.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/AddProperty.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/Clear.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/PropertyEditor.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/PropertyEditor.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/PropertyEditor.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/RemoveProperty.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/ts/PropertyEditor_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/ts/PropertyEditor_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/ts/PropertyEditor_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/ts/PropertyEditor_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/ts/PropertyEditor_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/ts/PropertyEditor_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/ts/PropertyEditor_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/PropertyEditor/ts/PropertyEditor_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/SelectionDisplay/SelectionDisplay.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/SelectionDisplay/SelectionDisplay.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/SelectionDisplay/SelectionDisplay.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/SelectionDisplay/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/SelectionDisplay/ts/SelectionDisplay_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/SelectionDisplay/ts/SelectionDisplay_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/SelectionDisplay/ts/SelectionDisplay_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/SelectionDisplay/ts/SelectionDisplay_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/SelectionDisplay/ts/SelectionDisplay_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/SelectionDisplay/ts/SelectionDisplay_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/SelectionDisplay/ts/SelectionDisplay_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/SelectionDisplay/ts/SelectionDisplay_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TabBar/TabBar.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TabBar/TabBar.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TabBar/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TabBar/ts/TabBar.pt.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TabBar/ts/TabBar.pt_BR.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TabBar/ts/TabBar_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TabBar/ts/TabBar_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TabBar/ts/TabBar_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TabBar/ts/TabBar_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TabBar/ts/TabBar_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TabBar/ts/TabBar_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TabBar/ts/TabBar_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TabBar/ts/TabBar_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TrialTeaser/TrialTeaser.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TrialTeaser/TrialTeaser.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TrialTeaser/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TrialTeaser/ts/TrialTeaser_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TrialTeaser/ts/TrialTeaser_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TrialTeaser/ts/TrialTeaser_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TrialTeaser/ts/TrialTeaser_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TrialTeaser/ts/TrialTeaser_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TrialTeaser/ts/TrialTeaser_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TrialTeaser/ts/TrialTeaser_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/TrialTeaser/ts/TrialTeaser_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ViewList/ViewList.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ViewList/ViewList.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ViewList/ViewList.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ViewList/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ViewList/ts/ViewList_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ViewList/ts/ViewList_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ViewList/ts/ViewList_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ViewList/ts/ViewList_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ViewList/ts/ViewList_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ViewList/ts/ViewList_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ViewList/ts/ViewList_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ViewList/ts/ViewList_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Viewport.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Viewport.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Viewport.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/00_Single.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/10_TwoVertical.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/11_TwoHorizontal.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/20_ThreeRight.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/21_ThreeLeft.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/22_ThreeAbove.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/23_ThreeBelow.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/24_ThreeVertical.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/25_ThreeHorizontal.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/30_FourEqual.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/31_FourRight.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/32_FourLeft.ui
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/DrawingLandscape.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/DrawingLandscapeZoom1.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/DrawingLandscapeZoom2.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/DrawingLandscapeZoom3.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/DrawingPortrait.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/DrawingPortraitZoom1.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/Templates/DrawingPortraitZoom2.svg
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/ts/Viewport_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/ts/Viewport_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/ts/Viewport_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/ts/Viewport_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/ts/Viewport_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/ts/Viewport_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/ts/Viewport_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/Viewport/ts/Viewport_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ts/Widgets.pt.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ts/Widgets.pt_BR.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ts/Widgets_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ts/Widgets_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ts/Widgets_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ts/Widgets_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ts/Widgets_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ts/Widgets_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ts/Widgets_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ts/Widgets_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Widgets/ts/ts.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Cascade
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/CloseAll
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/FullScreen
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Next
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Previous
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Tile
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Window.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Window.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/doc
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Cascade/Cascade.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Cascade/Cascade.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Cascade/doc
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Cascade/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Cascade/doc/Cascade.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Cascade/doc/Cascade_de.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Cascade/doc/Cascade_desc_en.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Cascade/ts/Cascade_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Cascade/ts/Cascade_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Cascade/ts/Cascade_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Cascade/ts/Cascade_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Cascade/ts/Cascade_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Cascade/ts/Cascade_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Cascade/ts/Cascade_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Cascade/ts/Cascade_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/CloseAll/CloseAll.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/CloseAll/CloseAll.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/CloseAll/doc
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/CloseAll/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/CloseAll/doc/CloseAll.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/CloseAll/doc/CloseAll_de.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/CloseAll/doc/CloseAll_desc_en.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/CloseAll/ts/CloseAll_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/CloseAll/ts/CloseAll_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/CloseAll/ts/CloseAll_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/CloseAll/ts/CloseAll_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/CloseAll/ts/CloseAll_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/CloseAll/ts/CloseAll_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/CloseAll/ts/CloseAll_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/CloseAll/ts/CloseAll_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/FullScreen/FullScreen.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/FullScreen/FullScreen.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/FullScreen/doc
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/FullScreen/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/FullScreen/doc/FullScreen.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/FullScreen/doc/FullScreen_de.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/FullScreen/doc/FullScreen_desc_en.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/FullScreen/ts/FullScreen_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/FullScreen/ts/FullScreen_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/FullScreen/ts/FullScreen_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/FullScreen/ts/FullScreen_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/FullScreen/ts/FullScreen_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/FullScreen/ts/FullScreen_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/FullScreen/ts/FullScreen_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/FullScreen/ts/FullScreen_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Next/Next.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Next/Next.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Next/doc
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Next/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Next/doc/Next.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Next/doc/Next_de.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Next/doc/Next_desc_en.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Next/ts/Next_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Next/ts/Next_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Next/ts/Next_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Next/ts/Next_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Next/ts/Next_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Next/ts/Next_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Next/ts/Next_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Next/ts/Next_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Previous/Previous.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Previous/Previous.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Previous/doc
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Previous/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Previous/doc/Previous.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Previous/doc/Previous_de.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Previous/doc/Previous_desc_en.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Previous/ts/Previous_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Previous/ts/Previous_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Previous/ts/Previous_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Previous/ts/Previous_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Previous/ts/Previous_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Previous/ts/Previous_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Previous/ts/Previous_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Previous/ts/Previous_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Tile/Tile.js
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Tile/Tile.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Tile/doc
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Tile/ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Tile/doc/Tile.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Tile/doc/Tile_de.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Tile/doc/Tile_desc_en.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Tile/ts/Tile_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Tile/ts/Tile_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Tile/ts/Tile_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Tile/ts/Tile_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Tile/ts/Tile_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Tile/ts/Tile_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Tile/ts/Tile_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/Tile/ts/Tile_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/doc/Window.html
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/ts/Window.pt.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/ts/Window.pt_BR.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/ts/Window_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/ts/Window_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/ts/Window_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/ts/Window_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/ts/Window_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/ts/Window_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/ts/Window_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/ts/Window_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/Window/ts/ts.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/ts/Scripts_de.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/ts/Scripts_de.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/ts/Scripts_es.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/ts/Scripts_es.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/ts/Scripts_fr.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/ts/Scripts_fr.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/ts/Scripts_it.qm
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/ts/Scripts_it.ts
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/scripts/ts/ts.pro
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/xdg/xdg-desktop-icon
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/xdg/xdg-desktop-menu
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/xdg/xdg-icon-resource
/home/clive/opt/qcad-3.0.0-rc2-prof-linux/xdg/xdg-mime
/usr/share/app-install/desktop/qcad:qcad.desktop
/usr/share/app-install/icons/qcad.png
```

---

### Post by MG&amp;TL on 2012-01-19
ah...okay, it seems that qcad has installed into your home folder,which is not normal...but not a problem.

I think what it means by the installation directory is /home/clive/opt/qcad-3.0.0-rc2-prof-linux/, but I could be wrong. Look in the opt folder, anyway.

---

### Post by ajgreeny on 2012-01-19
So everything except the last two files listed are in your home.

Look in your home for a folder called **/opt/qcad-3.0.0-rc2-prof-linux/** which is where everything seems to be, and go from there to do whatever it is that you need to do.  As it's all in home there should be no permission problems.

---

### Post by cliveT on 2012-01-19
OK thanks guys - yes I`ve found it as you said in the "opt" folder.

Thank you and regards

Clive :)

---


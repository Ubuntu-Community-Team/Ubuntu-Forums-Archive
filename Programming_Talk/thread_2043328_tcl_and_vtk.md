---
title: "tcl and vtk"
date: 2012-08-16
forum: Programming Talk
---

### Post by bigrockcrasher on 2012-08-16
I am currently trying to get tcl and vtk to work with each other. I have the tclvtk bindings as well as the bindings with c ,c++ and development package all installed through ubuntu's synaptic. after adding the correct directory to auto_path variable i get the following messege when i use the command "package require vtk":

couldn't load file "/usr//lib//libvtkRenderingTCL.so": /usr//lib//libvtkRenderingTCL.so: undefined symbol: _Z23vtkTclVoidFuncArgDeletePv
attempt to provide package vtkRenderingTCL 5.8 failed: no version of package vtkRenderingTCL provided
attempt to provide package vtkrendering 5.8 failed: no version of package vtkrendering provided
attempt to provide package vtk 5.8 failed: no version of package vtk provided


I am currently working with two computers one laptop and one desktop both using ubuntu 12.04, both return the same messege

---


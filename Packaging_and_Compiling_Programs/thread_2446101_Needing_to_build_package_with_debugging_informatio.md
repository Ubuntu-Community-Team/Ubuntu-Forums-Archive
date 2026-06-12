---
title: "Needing to build package with debugging information"
date: 2020-06-24
forum: Packaging and Compiling Programs
---

### Post by milantha on 2020-06-24
I am trying to rebuild the Mysql binaries on a Ubuntu Bionic system in order to include debugging information.  Specifically, I would like to use the mysqlimport command with the --debug option.  The base binaries do not have debugging enabled.

I have followed the general directions on this page: [https://www.cmiss.org/cmgui/wiki/BuildingUbuntuPackagesFromSource](https://www.cmiss.org/cmgui/wiki/BuildingUbuntuPackagesFromSource) for building an Ubuntu package from source. I am able to get all the way through the process of building the packages as-provided, but I am unable to figure out how to add the options that I need to the build process.

Addtionally, I have consulted the MySQL manual here: [https://dev.mysql.com/doc/refman/8.0/en/source-configuration-options.html#option_cmake_with_debug](https://dev.mysql.com/doc/refman/8.0/en/source-configuration-options.html#option_cmake_with_debug) .

I understand that I need to pass WITH_DEBUG to cmake, but I am not sure how to do so.  I have been searching unsuccessfully for several hours for a guide or instructions.

I would be extremely grateful for information on how to add this cmake option.

Thank you!

---


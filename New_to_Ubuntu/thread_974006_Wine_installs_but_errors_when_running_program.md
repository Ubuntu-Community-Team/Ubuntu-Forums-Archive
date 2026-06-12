---
title: "Wine installs but errors when running program"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Nempis on 2008-11-07
Hello people,

First of all I must anounce that my knowledge about ubuntu is minimal so please explain in realy a simple way and step by step.

My problem is that I was able to install civilization IV with wine succesfully but when I try to run the program it gives this message.

err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\python24.dll") not found
err:module:import_dll Library python24.dll (which is needed by L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\BOOST_PYTHON-VC71-MT-1_32.DLL") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\BOOST_PYTHON-VC71-MT-1_32.DLL") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\BOOST_PYTHON-VC71-MT-1_32.DLL") not found
err:module:import_dll Library BOOST_PYTHON-VC71-MT-1_32.DLL (which is needed by L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\Civilization4.exe") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\HAPDBG.DLL") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\python24.dll") not found
err:module:import_dll Library python24.dll (which is needed by L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\HAPDBG.DLL") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\HAPDBG.DLL") not found
err:module:import_dll Library HAPDBG.DLL (which is needed by L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\Civilization4.exe") not found
err:module:import_dll Library MSVCP71.DLL (which is needed by L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\Civilization4.exe") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\PYTHON24.DLL") not found
err:module:import_dll Library PYTHON24.DLL (which is needed by L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\Civilization4.exe") not found
err:module:import_dll Library MSVCR71.DLL (which is needed by L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\Civilization4.exe") not found
err:module:import_dll Library D3DX9_26.DLL (which is needed by L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\Civilization4.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\Civilization4.exe" failed, status c0000135

I gave the command "wine Civilization4.exe" in the directory where the program is in.

I have ubuntu 6.06 and wine 0.9.9

What should I do to make the program run properly?

---

### Post by Sarmacid on 2008-11-07
First, I would suggest getting a newer version of wine. Compiling it from source might be hard, but newer versions of ubuntu come with a newer version of wine, so you might consider upgrading ubuntu too.

When you try to run something in wine, you should check the wine appdb. It says there what works and what doesn't and usually tells how to get something to work. The entry for Civ4 is at [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2514](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2514)

---


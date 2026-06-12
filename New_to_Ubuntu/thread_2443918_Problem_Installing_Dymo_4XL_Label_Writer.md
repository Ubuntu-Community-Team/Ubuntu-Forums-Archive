---
title: "Problem Installing Dymo 4XL Label Writer"
date: 2020-05-22
forum: New to Ubuntu
---

### Post by anonymouscoward2 on 2020-05-22
I just installed the latest LTS (Ubuntu 20.04 LTS) on a computer previously running windows. I never got my Dymo 4XL to work on a Linux but it's been since 2012 I last tried that piece of hardware on anything but a Windows Box, they still sell these Dymo 4XLs today. The difference between a Dymo 4XL and a regular Dymo is it prints labels up to 4 inches wide, while some their other models regular do up to 2.5 inches wide. This allows for one piece shipping labels such as for USPS, FEDEX, UPS, etc.

What Ubuntu installs automatically is a generic labelwriter. If I look around, I might get a normal Dymo but stuck with 2.5 inch printing.

The newest article I'm following is from 2016:

[https://grimtech.net/dymo-4xl-on-ubuntu-14-04/](https://grimtech.net/dymo-4xl-on-ubuntu-14-04/)

I'm stuck on the **make** step in terminal.

The output is:

```

Making all in src
make[1]: Entering directory '/home/workerb/Downloads/dymo-cups-drivers-1.4.0.5/src'
make  all-recursive
make[2]: Entering directory '/home/workerb/Downloads/dymo-cups-drivers-1.4.0.5/src'
Making all in lw
make[3]: Entering directory '/home/workerb/Downloads/dymo-cups-drivers-1.4.0.5/src/lw'
Making all in tests
make[4]: Entering directory '/home/workerb/Downloads/dymo-cups-drivers-1.4.0.5/src/lw/tests'
make[4]: Nothing to be done for 'all'.
make[4]: Leaving directory '/home/workerb/Downloads/dymo-cups-drivers-1.4.0.5/src/lw/tests'
make[4]: Entering directory '/home/workerb/Downloads/dymo-cups-drivers-1.4.0.5/src/lw'
g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -MT raster2dymolw.o -MD -MP -MF .deps/raster2dymolw.Tpo -c -o raster2dymolw.o raster2dymolw.cpp
In file included from **raster2dymolw.cpp:37**:
**../common/CupsFilter.h:** In member function ‘**int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**)**’:
**../common/CupsFilter.h:135:10:** **[COLOR=#75507b]warning: [/COLOR]**‘**template<class> class std::auto_ptr**’ is deprecated [**[COLOR=#75507b]-Wdeprecated-declarations[/COLOR]**]
  135 |     std::**[COLOR=#75507b]auto_ptr[/COLOR]**<CHalftoneFilter> H;
      |          **[COLOR=#75507b]^~~~~~~~[/COLOR]**
In file included from **/usr/include/c++/9/memory:80**,
                 from **raster2dymolw.cpp:28**:
**/usr/include/c++/9/bits/unique_ptr.h:53:28:** **[COLOR=#06989a]note: [/COLOR]**declared here
   53 |   template<typename> class **[COLOR=#06989a]auto_ptr[/COLOR]**;
      |                            **[COLOR=#06989a]^~~~~~~~[/COLOR]**
In file included from **raster2dymolw.cpp:37**:
**../common/CupsFilter.h:** In member function ‘**void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*)**’:
**../common/CupsFilter.h:218:3:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppd_file_t**’ was not declared in this scope; did you mean ‘**cups_file_t**’?
  218 |   **[COLOR=#cc0000]ppd_file_t[/COLOR]*** ppd = ppdOpenFile(getenv("PPD"));
      |   **[COLOR=#cc0000]^~~~~~~~~~[/COLOR]**
      |   [COLOR=#4e9a06]cups_file_t[/COLOR]
**../common/CupsFilter.h:218:15:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppd**’ was not declared in this scope
  218 |   ppd_file_t* **[COLOR=#cc0000]ppd[/COLOR]** = ppdOpenFile(getenv("PPD"));
      |               **[COLOR=#cc0000]^~~[/COLOR]**
**../common/CupsFilter.h:218:21:** **[COLOR=#cc0000]error: [/COLOR]**there are no arguments to ‘**ppdOpenFile****[COLOR=#cc0000]’ that depend on a temp[/COLOR]**late parameter, so a declaration of ‘**ppdOpenFile**’ must be available [**[COLOR=#cc0000]-fpermissive[/COLOR]**]
  218 |   ppd_file_t* ppd = **[COLOR=#cc0000]ppdOpenFile[/COLOR]**(getenv("PPD"));
      |                     **[COLOR=#cc0000]^~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:218:21:** **[COLOR=#06989a]note: [/COLOR]**(if you use ‘**-fpermissive**’, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
**../common/CupsFilter.h:228:3:** **[COLOR=#cc0000]error: [/COLOR]**there are no arguments to ‘**ppdMarkDefaults****[COLOR=#cc0000]’ that depend on a t[/COLOR]**emplate parameter, so a declaration of ‘**ppdMarkDefaults**’ must be available [**[COLOR=#cc0000]-fpermissive[/COLOR]**]
  228 |   **[COLOR=#cc0000]ppdMarkDefaults[/COLOR]**(ppd);
      |   **[COLOR=#cc0000]^~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:234:7:** **[COLOR=#cc0000]error: [/COLOR]**there are no arguments to ‘**ppdMarkOption****[COLOR=#cc0000]’ that depend on a tem[/COLOR]**plate parameter, so a declaration of ‘**ppdMarkOption**’ must be available [**[COLOR=#cc0000]-fpermissive[/COLOR]**]
  234 |       **[COLOR=#cc0000]ppdMarkOption[/COLOR]**(ppd, Options[i].name, Options[i].value);
      |       **[COLOR=#cc0000]^~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:238:3:** **[COLOR=#cc0000]error: [/COLOR]**there are no arguments to ‘**cupsMarkOptions****[COLOR=#cc0000]’ that depend on a t[/COLOR]**emplate parameter, so a declaration of ‘**cupsMarkOptions**’ must be available [**[COLOR=#cc0000]-fpermissive[/COLOR]**]
  238 |   **[COLOR=#cc0000]cupsMarkOptions[/COLOR]**(ppd, OptionCount, Options);
      |   **[COLOR=#cc0000]^~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:243:3:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppd_choice_t**’ was not declared in this scope
  243 |   **[COLOR=#cc0000]ppd_choice_t[/COLOR]*** choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
      |   **[COLOR=#cc0000]^~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:243:17:** **[COLOR=#cc0000]error: [/COLOR]**‘**choice**’ was not declared in this scope
  243 |   ppd_choice_t* **[COLOR=#cc0000]choice[/COLOR]** = ppdFindMarkedChoice(ppd, "DymoHalftoning");
      |                 **[COLOR=#cc0000]^~~~~~[/COLOR]**
**../common/CupsFilter.h:243:26:** **[COLOR=#cc0000]error: [/COLOR]**there are no arguments to ‘**ppdFindMarkedChoice**’ that depend on a template parameter, so a declaration of ‘**ppdFindMarkedChoice**’ must be available [**[COLOR=#cc0000]-fpermissive[/COLOR]**]
  243 |   ppd_choice_t* choice = **[COLOR=#cc0000]ppdFindMarkedChoice[/COLOR]**(ppd, "DymoHalftoning");
      |                          **[COLOR=#cc0000]^~~~~~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:248:3:** **[COLOR=#cc0000]error: [/COLOR]**there are no arguments to ‘**ppdClose****[COLOR=#cc0000]’ that depend on a template[/COLOR]** parameter, so a declaration of ‘**ppdClose**’ must be available [**[COLOR=#cc0000]-fpermissive[/COLOR]**]
  248 |   **[COLOR=#cc0000]ppdClose[/COLOR]**(ppd);
      |   **[COLOR=#cc0000]^~~~~~~~[/COLOR]**
In file included from **raster2dymolw.cpp:38**:
**CupsFilterLabelWriter.h:** At global scope:
**CupsFilterLabelWriter.h:36:89:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppd_file_t**’ has not been declared
   36 | c void ProcessPPDOptions (CLabelWriterDriver& Driver, CDummyLanguageMonitor& LM, **[COLOR=#cc0000]ppd_file_t[/COLOR]*** ppd);
      |                                                                                  **[COLOR=#cc0000]^~~~~~~~~~[/COLOR]**

**CupsFilterLabelWriter.h:43:98:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppd_file_t**’ has not been declared
   43 | ocessPPDOptions (CLabelWriterDriverTwinTurbo& Driver, CDummyLanguageMonitor& LM, **[COLOR=#cc0000]ppd_file_t[/COLOR]*** ppd);
      |                                                                                  **[COLOR=#cc0000]^~~~~~~~~~[/COLOR]**

In file included from **raster2dymolw.cpp:38**:
**CupsFilterLabelWriter.h:50:95:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppd_file_t**’ has not been declared
   50 |  ProcessPPDOptions (CLabelWriterDriver& Driver, CLabelWriterLanguageMonitor& LM, **[COLOR=#cc0000]ppd_file_t[/COLOR]*** ppd);
      |                                                                                  **[COLOR=#cc0000]^~~~~~~~~~[/COLOR]**

**CupsFilterLabelWriter.h:58:104:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppd_file_t**’ has not been declared
   58 | PDOptions (CLabelWriterDriverTwinTurbo& Driver, CLabelWriterLanguageMonitor& LM, **[COLOR=#cc0000]ppd_file_t[/COLOR]*** ppd);
      |                                                                                  **[COLOR=#cc0000]^~~~~~~~~~[/COLOR]**

**raster2dymolw.cpp:** In function ‘**int main(int, char**)**’:
**raster2dymolw.cpp:60:3:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppd_file_t**’ was not declared in this scope; did you mean ‘**cups_file_t**’?
   60 |   **[COLOR=#cc0000]ppd_file_t[/COLOR]*** ppd = ppdOpenFile(getenv("PPD"));
      |   **[COLOR=#cc0000]^~~~~~~~~~[/COLOR]**
      |   [COLOR=#4e9a06]cups_file_t[/COLOR]
**raster2dymolw.cpp:60:15:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppd**’ was not declared in this scope
   60 |   ppd_file_t* **[COLOR=#cc0000]ppd[/COLOR]** = ppdOpenFile(getenv("PPD"));
      |               **[COLOR=#cc0000]^~~[/COLOR]**
**raster2dymolw.cpp:60:21:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdOpenFile**’ was not declared in this scope
   60 |   ppd_file_t* ppd = **[COLOR=#cc0000]ppdOpenFile[/COLOR]**(getenv("PPD"));
      |                     **[COLOR=#cc0000]^~~~~~~~~~~[/COLOR]**
In file included from **raster2dymolw.cpp:37**:
../common/CupsFilter.h: In instantiation of ‘**void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*) [with D = DymoPrinterDriver::CLabelWriterDriver; DI = DymoPrinterDriver::CDriverInitializerLabelWriterWithLM; LM = DymoPrinterDriver::CLabelWriterLanguageMonitor]**’:
**../common/CupsFilter.h:99:3:**   required from ‘**int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**) [with D = DymoPrinterDriver::CLabelWriterDriver; DI = DymoPrinterDriver::CDriverInitializerLabelWriterWithLM; LM = DymoPrinterDriver::CLabelWriterLanguageMonitor]**’
**raster2dymolw.cpp:68:35:**   required from here
**../common/CupsFilter.h:218:32:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdOpenFile**’ was not declared in this scope
  218 |   ppd_file_t* ppd = **[COLOR=#cc0000]ppdOpenFile(getenv("PPD"))[/COLOR]**;
      |                     **[COLOR=#cc0000]~~~~~~~~~~~^~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:228:18:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdMarkDefaults**’ was not declared in this scope
  228 |   **[COLOR=#cc0000]ppdMarkDefaults(ppd)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~~~~~~~~^~~~~[/COLOR]**
**../common/CupsFilter.h:234:20:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdMarkOption**’ was not declared in this scope
  234 |       **[COLOR=#cc0000]ppdMarkOption(ppd, Options[i].name, Options[i].value)[/COLOR]**;
      |       **[COLOR=#cc0000]~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:238:18:** **[COLOR=#cc0000]error: [/COLOR]**‘**cupsMarkOptions**’ was not declared in this scope; did you mean ‘**cupsParseOptions**’?
  238 |   **[COLOR=#cc0000]cupsMarkOptions(ppd, OptionCount, Options)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
      |   [COLOR=#4e9a06]cupsParseOptions[/COLOR]
**../common/CupsFilter.h:243:45:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdFindMarkedChoice**’ was not declared in this scope
  243 |   ppd_choice_t* choice = **[COLOR=#cc0000]ppdFindMarkedChoice(ppd, "DymoHalftoning")[/COLOR]**;
      |                          **[COLOR=#cc0000]~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:248:11:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdClose**’ was not declared in this scope; did you mean ‘**pclose**’?
  248 |   **[COLOR=#cc0000]ppdClose(ppd)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~^~~~~[/COLOR]**
      |   [COLOR=#4e9a06]pclose[/COLOR]
../common/CupsFilter.h: In instantiation of ‘**void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*) [with D = DymoPrinterDriver::CLabelWriterDriver; DI = DymoPrinterDriver::CDriverInitializerLabelWriter; LM = DymoPrinterDriver::CDummyLanguageMonitor]**’:
**../common/CupsFilter.h:99:3:**   required from ‘**int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**) [with D = DymoPrinterDriver::CLabelWriterDriver; DI = DymoPrinterDriver::CDriverInitializerLabelWriter; LM = DymoPrinterDriver::CDummyLanguageMonitor]**’
**raster2dymolw.cpp:73:35:**   required from here
**../common/CupsFilter.h:218:32:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdOpenFile**’ was not declared in this scope
  218 |   ppd_file_t* ppd = **[COLOR=#cc0000]ppdOpenFile(getenv("PPD"))[/COLOR]**;
      |                     **[COLOR=#cc0000]~~~~~~~~~~~^~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:228:18:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdMarkDefaults**’ was not declared in this scope
  228 |   **[COLOR=#cc0000]ppdMarkDefaults(ppd)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~~~~~~~~^~~~~[/COLOR]**
**../common/CupsFilter.h:234:20:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdMarkOption**’ was not declared in this scope
  234 |       **[COLOR=#cc0000]ppdMarkOption(ppd, Options[i].name, Options[i].value)[/COLOR]**;
      |       **[COLOR=#cc0000]~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:238:18:** **[COLOR=#cc0000]error: [/COLOR]**‘**cupsMarkOptions**’ was not declared in this scope; did you mean ‘**cupsParseOptions**’?
  238 |   **[COLOR=#cc0000]cupsMarkOptions(ppd, OptionCount, Options)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
      |   [COLOR=#4e9a06]cupsParseOptions[/COLOR]
**../common/CupsFilter.h:243:45:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdFindMarkedChoice**’ was not declared in this scope
  243 |   ppd_choice_t* choice = **[COLOR=#cc0000]ppdFindMarkedChoice(ppd, "DymoHalftoning")[/COLOR]**;
      |                          **[COLOR=#cc0000]~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:248:11:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdClose**’ was not declared in this scope; did you mean ‘**pclose**’?
  248 |   **[COLOR=#cc0000]ppdClose(ppd)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~^~~~~[/COLOR]**
      |   [COLOR=#4e9a06]pclose[/COLOR]
../common/CupsFilter.h: In instantiation of ‘**void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*) [with D = DymoPrinterDriver::CLabelWriterDriverTwinTurbo; DI = DymoPrinterDriver::CDriverInitializerLabelWriterTwinTurboWithLM; LM = DymoPrinterDriver::CLabelWriterLanguageMonitor]**’:
**../common/CupsFilter.h:99:3:**   required from ‘**int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**) [with D = DymoPrinterDriver::CLabelWriterDriverTwinTurbo; DI = DymoPrinterDriver::CDriverInitializerLabelWriterTwinTurboWithLM; LM = DymoPrinterDriver::CLabelWriterLanguageMonitor]**’
**raster2dymolw.cpp:84:37:**   required from here
**../common/CupsFilter.h:218:32:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdOpenFile**’ was not declared in this scope
  218 |   ppd_file_t* ppd = **[COLOR=#cc0000]ppdOpenFile(getenv("PPD"))[/COLOR]**;
      |                     **[COLOR=#cc0000]~~~~~~~~~~~^~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:228:18:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdMarkDefaults**’ was not declared in this scope
  228 |   **[COLOR=#cc0000]ppdMarkDefaults(ppd)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~~~~~~~~^~~~~[/COLOR]**
**../common/CupsFilter.h:234:20:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdMarkOption**’ was not declared in this scope
  234 |       **[COLOR=#cc0000]ppdMarkOption(ppd, Options[i].name, Options[i].value)[/COLOR]**;
      |       **[COLOR=#cc0000]~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:238:18:** **[COLOR=#cc0000]error: [/COLOR]**‘**cupsMarkOptions**’ was not declared in this scope; did you mean ‘**cupsParseOptions**’?
  238 |   **[COLOR=#cc0000]cupsMarkOptions(ppd, OptionCount, Options)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
      |   [COLOR=#4e9a06]cupsParseOptions[/COLOR]
**../common/CupsFilter.h:243:45:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdFindMarkedChoice**’ was not declared in this scope
  243 |   ppd_choice_t* choice = **[COLOR=#cc0000]ppdFindMarkedChoice(ppd, "DymoHalftoning")[/COLOR]**;
      |                          **[COLOR=#cc0000]~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:248:11:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdClose**’ was not declared in this scope; did you mean ‘**pclose**’?
  248 |   **[COLOR=#cc0000]ppdClose(ppd)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~^~~~~[/COLOR]**
      |   [COLOR=#4e9a06]pclose[/COLOR]
../common/CupsFilter.h: In instantiation of ‘**void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*) [with D = DymoPrinterDriver::CLabelWriterDriverTwinTurbo; DI = DymoPrinterDriver::CDriverInitializerLabelWriterTwinTurbo; LM = DymoPrinterDriver::CDummyLanguageMonitor]**’:
**../common/CupsFilter.h:99:3:**   required from ‘**int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**) [with D = DymoPrinterDriver::CLabelWriterDriverTwinTurbo; DI = DymoPrinterDriver::CDriverInitializerLabelWriterTwinTurbo; LM = DymoPrinterDriver::CDummyLanguageMonitor]**’
**raster2dymolw.cpp:89:37:**   required from here
**../common/CupsFilter.h:218:32:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdOpenFile**’ was not declared in this scope
  218 |   ppd_file_t* ppd = **[COLOR=#cc0000]ppdOpenFile(getenv("PPD"))[/COLOR]**;
      |                     **[COLOR=#cc0000]~~~~~~~~~~~^~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:228:18:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdMarkDefaults**’ was not declared in this scope
  228 |   **[COLOR=#cc0000]ppdMarkDefaults(ppd)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~~~~~~~~^~~~~[/COLOR]**
**../common/CupsFilter.h:234:20:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdMarkOption**’ was not declared in this scope
  234 |       **[COLOR=#cc0000]ppdMarkOption(ppd, Options[i].name, Options[i].value)[/COLOR]**;
      |       **[COLOR=#cc0000]~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:238:18:** **[COLOR=#cc0000]error: [/COLOR]**‘**cupsMarkOptions**’ was not declared in this scope; did you mean ‘**cupsParseOptions**’?
  238 |   **[COLOR=#cc0000]cupsMarkOptions(ppd, OptionCount, Options)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
      |   [COLOR=#4e9a06]cupsParseOptions[/COLOR]
**../common/CupsFilter.h:243:45:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdFindMarkedChoice**’ was not declared in this scope
  243 |   ppd_choice_t* choice = **[COLOR=#cc0000]ppdFindMarkedChoice(ppd, "DymoHalftoning")[/COLOR]**;
      |                          **[COLOR=#cc0000]~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:248:11:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdClose**’ was not declared in this scope; did you mean ‘**pclose**’?
  248 |   **[COLOR=#cc0000]ppdClose(ppd)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~^~~~~[/COLOR]**
      |   [COLOR=#4e9a06]pclose[/COLOR]
../common/CupsFilter.h: In instantiation of ‘**void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*) [with D = DymoPrinterDriver::CLabelWriterDriver400; DI = DymoPrinterDriver::CDriverInitializerLabelWriterWithLM; LM = DymoPrinterDriver::CLabelWriterLanguageMonitor]**’:
**../common/CupsFilter.h:99:3:**   required from ‘**int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**) [with D = DymoPrinterDriver::CLabelWriterDriver400; DI = DymoPrinterDriver::CDriverInitializerLabelWriterWithLM; LM = DymoPrinterDriver::CLabelWriterLanguageMonitor]**’
**raster2dymolw.cpp:103:37:**   required from here
**../common/CupsFilter.h:218:32:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdOpenFile**’ was not declared in this scope
  218 |   ppd_file_t* ppd = **[COLOR=#cc0000]ppdOpenFile(getenv("PPD"))[/COLOR]**;
      |                     **[COLOR=#cc0000]~~~~~~~~~~~^~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:228:18:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdMarkDefaults**’ was not declared in this scope
  228 |   **[COLOR=#cc0000]ppdMarkDefaults(ppd)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~~~~~~~~^~~~~[/COLOR]**
**../common/CupsFilter.h:234:20:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdMarkOption**’ was not declared in this scope
  234 |       **[COLOR=#cc0000]ppdMarkOption(ppd, Options[i].name, Options[i].value)[/COLOR]**;
      |       **[COLOR=#cc0000]~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:238:18:** **[COLOR=#cc0000]error: [/COLOR]**‘**cupsMarkOptions**’ was not declared in this scope; did you mean ‘**cupsParseOptions**’?
  238 |   **[COLOR=#cc0000]cupsMarkOptions(ppd, OptionCount, Options)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
      |   [COLOR=#4e9a06]cupsParseOptions[/COLOR]
**../common/CupsFilter.h:243:45:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdFindMarkedChoice**’ was not declared in this scope
  243 |   ppd_choice_t* choice = **[COLOR=#cc0000]ppdFindMarkedChoice(ppd, "DymoHalftoning")[/COLOR]**;
      |                          **[COLOR=#cc0000]~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:248:11:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdClose**’ was not declared in this scope; did you mean ‘**pclose**’?
  248 |   **[COLOR=#cc0000]ppdClose(ppd)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~^~~~~[/COLOR]**
      |   [COLOR=#4e9a06]pclose[/COLOR]
../common/CupsFilter.h: In instantiation of ‘**void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*) [with D = DymoPrinterDriver::CLabelWriterDriver400; DI = DymoPrinterDriver::CDriverInitializerLabelWriter; LM = DymoPrinterDriver::CDummyLanguageMonitor]**’:
**../common/CupsFilter.h:99:3:**   required from ‘**int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**) [with D = DymoPrinterDriver::CLabelWriterDriver400; DI = DymoPrinterDriver::CDriverInitializerLabelWriter; LM = DymoPrinterDriver::CDummyLanguageMonitor]**’
**raster2dymolw.cpp:108:37:**   required from here
**../common/CupsFilter.h:218:32:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdOpenFile**’ was not declared in this scope
  218 |   ppd_file_t* ppd = **[COLOR=#cc0000]ppdOpenFile(getenv("PPD"))[/COLOR]**;
      |                     **[COLOR=#cc0000]~~~~~~~~~~~^~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:228:18:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdMarkDefaults**’ was not declared in this scope
  228 |   **[COLOR=#cc0000]ppdMarkDefaults(ppd)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~~~~~~~~^~~~~[/COLOR]**
**../common/CupsFilter.h:234:20:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdMarkOption**’ was not declared in this scope
  234 |       **[COLOR=#cc0000]ppdMarkOption(ppd, Options[i].name, Options[i].value)[/COLOR]**;
      |       **[COLOR=#cc0000]~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:238:18:** **[COLOR=#cc0000]error: [/COLOR]**‘**cupsMarkOptions**’ was not declared in this scope; did you mean ‘**cupsParseOptions**’?
  238 |   **[COLOR=#cc0000]cupsMarkOptions(ppd, OptionCount, Options)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
      |   [COLOR=#4e9a06]cupsParseOptions[/COLOR]
**../common/CupsFilter.h:243:45:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdFindMarkedChoice**’ was not declared in this scope
  243 |   ppd_choice_t* choice = **[COLOR=#cc0000]ppdFindMarkedChoice(ppd, "DymoHalftoning")[/COLOR]**;
      |                          **[COLOR=#cc0000]~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~[/COLOR]**
**../common/CupsFilter.h:248:11:** **[COLOR=#cc0000]error: [/COLOR]**‘**ppdClose**’ was not declared in this scope; did you mean ‘**pclose**’?
  248 |   **[COLOR=#cc0000]ppdClose(ppd)[/COLOR]**;
      |   **[COLOR=#cc0000]~~~~~~~~^~~~~[/COLOR]**
      |   [COLOR=#4e9a06]pclose[/COLOR]
make[4]: *** [Makefile:345: raster2dymolw.o] Error 1
make[4]: Leaving directory '/home/workerb/Downloads/dymo-cups-drivers-1.4.0.5/src/lw'
make[3]: *** [Makefile:435: all-recursive] Error 1
make[3]: Leaving directory '/home/workerb/Downloads/dymo-cups-drivers-1.4.0.5/src/lw'
make[2]: *** [Makefile:262: all-recursive] Error 1
make[2]: Leaving directory '/home/workerb/Downloads/dymo-cups-drivers-1.4.0.5/src'
make[1]: *** [Makefile:204: all] Error 2
make[1]: Leaving directory '/home/workerb/Downloads/dymo-cups-drivers-1.4.0.5/src'
make: *** [Makefile:263: all-recursive] Error 1

```

I tried the fixes at the bottom of the article, which got me a good ./configure result I was previously having problems with, but now I'm stuck.

Any help please?

---


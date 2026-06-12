---
title: "&quot;The Following Packages Have Been Kept Back&quot; - Mono"
date: 2016-06-16
forum: New to Ubuntu
---

### Post by Jordan_Bentley on 2016-06-16
Hi all,

Using Ubuntu 14.04 here - and a new user. I installed mono from the official repository and now whenever I run "sudo apt-get upgrade" I get the following message:

```
sudo apt-get upgradeReading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  ca-certificates-mono libmono-2.0-1 libmono-2.0-dev
  libmono-accessibility4.0-cil libmono-cairo4.0-cil libmono-cecil-private-cil
  libmono-cil-dev libmono-codecontracts4.0-cil
  libmono-compilerservices-symbolwriter4.0-cil libmono-corlib4.0-cil
  libmono-corlib4.5-cil libmono-cscompmgd0.0-cil libmono-csharp4.0c-cil
  libmono-custommarshalers4.0-cil libmono-data-tds4.0-cil libmono-db2-1.0-cil
  libmono-debugger-soft4.0a-cil libmono-http4.0-cil libmono-i18n-cjk4.0-cil
  libmono-i18n-mideast4.0-cil libmono-i18n-other4.0-cil
  libmono-i18n-rare4.0-cil libmono-i18n-west4.0-cil libmono-i18n4.0-all
  libmono-i18n4.0-cil libmono-ldap4.0-cil libmono-management4.0-cil
  libmono-messaging-rabbitmq4.0-cil libmono-messaging4.0-cil
  libmono-microsoft-build-engine4.0-cil
  libmono-microsoft-build-framework4.0-cil
  libmono-microsoft-build-tasks-v4.0-4.0-cil
  libmono-microsoft-build-utilities-v4.0-4.0-cil
  libmono-microsoft-build4.0-cil libmono-microsoft-csharp4.0-cil
  libmono-microsoft-visualc10.0-cil
  libmono-microsoft-web-infrastructure1.0-cil libmono-oracle4.0-cil
  libmono-parallel4.0-cil libmono-peapi4.0a-cil libmono-posix4.0-cil
  libmono-profiler libmono-rabbitmq4.0-cil libmono-relaxng4.0-cil
  libmono-security4.0-cil libmono-sharpzip4.84-cil libmono-simd4.0-cil
  libmono-smdiagnostics0.0-cil libmono-sqlite4.0-cil
  libmono-system-componentmodel-composition4.0-cil
  libmono-system-componentmodel-dataannotations4.0-cil
  libmono-system-configuration-install4.0-cil
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil
  libmono-system-data-datasetextensions4.0-cil
  libmono-system-data-entity4.0-cil libmono-system-data-linq4.0-cil
  libmono-system-data-services-client4.0-cil
  libmono-system-data-services4.0-cil libmono-system-data4.0-cil
  libmono-system-design4.0-cil libmono-system-drawing-design4.0-cil
  libmono-system-drawing4.0-cil libmono-system-dynamic4.0-cil
  libmono-system-enterpriseservices4.0-cil
  libmono-system-identitymodel-selectors4.0-cil
  libmono-system-identitymodel4.0-cil
  libmono-system-io-compression-filesystem4.0-cil
  libmono-system-io-compression4.0-cil libmono-system-json-microsoft4.0-cil
  libmono-system-json4.0-cil libmono-system-ldap-protocols4.0-cil
  libmono-system-ldap4.0-cil libmono-system-management4.0-cil
  libmono-system-messaging4.0-cil libmono-system-net-http-formatting4.0-cil
  libmono-system-net-http-webrequest4.0-cil libmono-system-net-http4.0-cil
  libmono-system-net4.0-cil libmono-system-numerics4.0-cil
  libmono-system-reactive-core2.2-cil libmono-system-reactive-debugger2.2-cil
  libmono-system-reactive-experimental2.2-cil
  libmono-system-reactive-interfaces2.2-cil
  libmono-system-reactive-linq2.2-cil
  libmono-system-reactive-observable-aliases0.0-cil
  libmono-system-reactive-platformservices2.2-cil
  libmono-system-reactive-providers2.2-cil
  libmono-system-reactive-runtime-remoting2.2-cil
  libmono-system-reactive-windows-forms2.2-cil
  libmono-system-reactive-windows-threading2.2-cil
  libmono-system-runtime-caching4.0-cil
  libmono-system-runtime-durableinstancing4.0-cil
  libmono-system-runtime-serialization-formatters-soap4.0-cil
  libmono-system-runtime-serialization4.0-cil libmono-system-runtime4.0-cil
  libmono-system-security4.0-cil libmono-system-servicemodel-activation4.0-cil
  libmono-system-servicemodel-discovery4.0-cil
  libmono-system-servicemodel-internals0.0-cil
  libmono-system-servicemodel-routing4.0-cil
  libmono-system-servicemodel-web4.0-cil libmono-system-servicemodel4.0a-cil
  libmono-system-serviceprocess4.0-cil
  libmono-system-threading-tasks-dataflow4.0-cil
  libmono-system-transactions4.0-cil libmono-system-web-abstractions4.0-cil
  libmono-system-web-applicationservices4.0-cil
  libmono-system-web-dynamicdata4.0-cil
  libmono-system-web-extensions-design4.0-cil
  libmono-system-web-extensions4.0-cil libmono-system-web-http-selfhost4.0-cil
  libmono-system-web-http-webhost4.0-cil libmono-system-web-http4.0-cil
  libmono-system-web-mvc3.0-cil libmono-system-web-razor2.0-cil
  libmono-system-web-routing4.0-cil libmono-system-web-services4.0-cil
  libmono-system-web-webpages-deployment2.0-cil
  libmono-system-web-webpages-razor2.0-cil libmono-system-web-webpages2.0-cil
  libmono-system-web4.0-cil
  libmono-system-windows-forms-datavisualization4.0a-cil
  libmono-system-windows-forms4.0-cil libmono-system-windows4.0-cil
  libmono-system-xaml4.0-cil libmono-system-xml-linq4.0-cil
  libmono-system-xml-serialization4.0-cil libmono-system-xml4.0-cil
  libmono-system4.0-cil libmono-tasklets4.0-cil libmono-webbrowser4.0-cil
  libmono-webmatrix-data4.0-cil libmono-windowsbase4.0-cil
  libmono-xbuild-tasks4.0-cil libmonoboehm-2.0-1 libmonoboehm-2.0-dev
  libnunit-cil-dev mono-4.0-gac mono-4.0-service mono-complete
  mono-csharp-shell mono-devel mono-gac mono-jay mono-mcs mono-runtime
  mono-runtime-common mono-runtime-sgen mono-utils mono-xbuild monodoc-base
  monodoc-manual
0 upgraded, 0 newly installed, 0 to remove and 153 not upgraded.

```

Any idea why this is happening and how I resolve it? 

Thank you :)

---

### Post by X-RED_Tech on 2016-06-16
Running ```
sudo apt-get dist-upgrade
```
should fully update the held back packages.

---

### Post by Jordan_Bentley on 2016-06-16
> **X-RED_Tech said:**
> Running ```
sudo apt-get dist-upgrade
```
should fully update the held back packages.

Thank you! Is there any danger of running this command on 14.04? It won't upgrade my Ubuntu version will it? (I need to keep 14.04 on my server)

---

### Post by slickymaster on 2016-06-16
> **Jordan_Bentley said:**
> Thank you! Is there any danger of running this command on 14.04? It won't upgrade my Ubuntu version will it? (I need to keep 14.04 on my server)

No, it won't upgrade your Ubuntu version. From **man apt-get**```
dist-upgrade
   dist-upgrade in addition to performing the function of upgrade,
   also intelligently handles changing dependencies with new versions
   of packages; apt-get has a "smart" conflict resolution system, and
   it will attempt to upgrade the most important packages at the
   expense of less important ones if necessary. So, dist-upgrade
   command may remove some packages. The /etc/apt/sources.list file
   contains a list of locations from which to retrieve desired package
   files. See also apt_preferences(5) for a mechanism for overriding
   the general settings for individual packages.
```

---

### Post by Jordan_Bentley on 2016-06-16
Thank you both - much appreciated!!

---


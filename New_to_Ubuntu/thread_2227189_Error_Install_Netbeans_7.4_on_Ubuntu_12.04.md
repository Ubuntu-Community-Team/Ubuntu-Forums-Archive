---
title: "Error Install Netbeans 7.4 on Ubuntu 12.04"
date: 2014-05-31
forum: New to Ubuntu
---

### Post by indi on 2014-05-31
Hi,

I don't know is this the correct place to ask, but I am posting hoping a help..

I tried to install Netbeans 7.4 on Ubuntu 12.04 running on VBox. While the installation wizard encounter error and crashes.

Here is what log says:

```
extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-sendopts.xml
[2014-05-31 17:23:03.402]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-sendopts.xml
[2014-05-31 17:23:03.402]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-masterfs.xml
[2014-05-31 17:23:03.403]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-masterfs.xml
[2014-05-31 17:23:03.406]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-netbinox.xml
[2014-05-31 17:23:03.407]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-netbinox.xml
[2014-05-31 17:23:03.407]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-settings.xml
[2014-05-31 17:23:03.407]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-settings.xml
[2014-05-31 17:23:03.408]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-swing-tabcontrol.xml
[2014-05-31 17:23:03.408]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-swing-tabcontrol.xml
[2014-05-31 17:23:03.408]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-javahelp.xml
[2014-05-31 17:23:03.409]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-javahelp.xml
[2014-05-31 17:23:03.413]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-core-kit.xml
[2014-05-31 17:23:03.413]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-core-kit.xml
[2014-05-31 17:23:03.420]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-openide-util-enumerations.xml
[2014-05-31 17:23:03.421]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-openide-util-enumerations.xml
[2014-05-31 17:23:03.426]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-execution.xml
[2014-05-31 17:23:03.426]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-execution.xml
[2014-05-31 17:23:03.429]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-multiview.xml
[2014-05-31 17:23:03.429]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-multiview.xml
[2014-05-31 17:23:03.436]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-multitabs.xml
[2014-05-31 17:23:03.437]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-multitabs.xml
[2014-05-31 17:23:03.444]:         extracting /usr/local/netbeans-7.4/platform/modules/locale/org-openide-nodes_ja.jar.pack.gz
[2014-05-31 17:23:03.445]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/locale/org-openide-nodes_ja.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/locale/org-openide-nodes_ja.jar, in directory: .
[2014-05-31 17:23:03.481]:             [return]: 0
[2014-05-31 17:23:03.481]:         ... command execution finished
[2014-05-31 17:23:03.481]:         deleting file: /usr/local/netbeans-7.4/platform/modules/locale/org-openide-nodes_ja.jar.pack.gz
[2014-05-31 17:23:03.482]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/locale/org-openide-nodes_ja.jar
[2014-05-31 17:23:03.482]:         extracting /usr/local/netbeans-7.4/platform/modules/locale/org-netbeans-core_ru.jar.pack.gz
[2014-05-31 17:23:03.483]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/locale/org-netbeans-core_ru.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/locale/org-netbeans-core_ru.jar, in directory: .
[2014-05-31 17:23:03.519]:             [return]: 0
[2014-05-31 17:23:03.520]:         ... command execution finished
[2014-05-31 17:23:03.520]:         deleting file: /usr/local/netbeans-7.4/platform/modules/locale/org-netbeans-core_ru.jar.pack.gz
[2014-05-31 17:23:03.520]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/locale/org-netbeans-core_ru.jar
[2014-05-31 17:23:03.520]:         extracting /usr/local/netbeans-7.4/platform/modules/locale/org-openide-nodes_ru.jar.pack.gz
[2014-05-31 17:23:03.525]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/locale/org-openide-nodes_ru.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/locale/org-openide-nodes_ru.jar, in directory: .
[2014-05-31 17:23:03.563]:             [return]: 0
[2014-05-31 17:23:03.563]:         ... command execution finished
[2014-05-31 17:23:03.563]:         deleting file: /usr/local/netbeans-7.4/platform/modules/locale/org-openide-nodes_ru.jar.pack.gz
[2014-05-31 17:23:03.564]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/locale/org-openide-nodes_ru.jar
[2014-05-31 17:23:03.564]:         extracting /usr/local/netbeans-7.4/platform/modules/locale/org-netbeans-core_ja.jar.pack.gz
[2014-05-31 17:23:03.565]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/locale/org-netbeans-core_ja.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/locale/org-netbeans-core_ja.jar, in directory: .
[2014-05-31 17:23:03.601]:             [return]: 0
[2014-05-31 17:23:03.601]:         ... command execution finished
[2014-05-31 17:23:03.602]:         deleting file: /usr/local/netbeans-7.4/platform/modules/locale/org-netbeans-core_ja.jar.pack.gz
[2014-05-31 17:23:03.602]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/locale/org-netbeans-core_ja.jar
[2014-05-31 17:23:03.603]:         extracting /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_zh_CN.jar.pack.gz
[2014-05-31 17:23:03.604]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_zh_CN.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_zh_CN.jar, in directory: .
[2014-05-31 17:23:03.624]:             [return]: 0
[2014-05-31 17:23:03.624]:         ... command execution finished
[2014-05-31 17:23:03.624]:         deleting file: /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_zh_CN.jar.pack.gz
[2014-05-31 17:23:03.624]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_zh_CN.jar
[2014-05-31 17:23:03.624]:         extracting /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_pt_BR.jar.pack.gz
[2014-05-31 17:23:03.631]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_pt_BR.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_pt_BR.jar, in directory: .
[2014-05-31 17:23:03.649]:             [return]: 0
[2014-05-31 17:23:03.649]:         ... command execution finished
[2014-05-31 17:23:03.649]:         deleting file: /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_pt_BR.jar.pack.gz
[2014-05-31 17:23:03.649]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_pt_BR.jar
[2014-05-31 17:23:03.650]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-multitabs.jar.pack.gz
[2014-05-31 17:23:03.651]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-multitabs.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-multitabs.jar, in directory: .
[2014-05-31 17:23:03.687]:             [return]: 0
[2014-05-31 17:23:03.687]:         ... command execution finished
[2014-05-31 17:23:03.687]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-multitabs.jar.pack.gz
[2014-05-31 17:23:03.687]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-multitabs.jar
[2014-05-31 17:23:03.690]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-execution.jar.pack.gz
[2014-05-31 17:23:03.691]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-execution.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-execution.jar, in directory: .
[2014-05-31 17:23:03.724]:             [return]: 0
[2014-05-31 17:23:03.725]:         ... command execution finished
[2014-05-31 17:23:03.725]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-execution.jar.pack.gz
[2014-05-31 17:23:03.725]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-execution.jar
[2014-05-31 17:23:03.726]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-multiview.jar.pack.gz
[2014-05-31 17:23:03.727]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-multiview.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-multiview.jar, in directory: .
[2014-05-31 17:23:03.783]:             [return]: 0
[2014-05-31 17:23:03.783]:         ... command execution finished
[2014-05-31 17:23:03.783]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-multiview.jar.pack.gz
[2014-05-31 17:23:03.784]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-multiview.jar
[2014-05-31 17:23:03.785]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-queries.xml
[2014-05-31 17:23:03.787]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-queries.xml
[2014-05-31 17:23:03.788]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-keyring.xml
[2014-05-31 17:23:03.788]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-keyring.xml
[2014-05-31 17:23:03.788]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-spi-quicksearch.xml
[2014-05-31 17:23:03.789]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-spi-quicksearch.xml
[2014-05-31 17:23:03.789]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-sampler.xml
[2014-05-31 17:23:03.795]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-sampler.xml
[2014-05-31 17:23:03.795]:         extracting /usr/local/netbeans-7.4/platform/config/ModuleAutoDeps/org-openide-execution.xml
[2014-05-31 17:23:03.796]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/ModuleAutoDeps/org-openide-execution.xml
[2014-05-31 17:23:03.796]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-modules-print.xml
[2014-05-31 17:23:03.797]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-modules-print.xml
[2014-05-31 17:23:03.797]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-lib-uihandler.xml
[2014-05-31 17:23:03.801]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-lib-uihandler.xml
[2014-05-31 17:23:03.805]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-swing-outline.xml
[2014-05-31 17:23:03.806]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-swing-outline.xml
[2014-05-31 17:23:03.810]:         extracting /usr/local/netbeans-7.4/platform/modules/locale/org-openide-text_ja.jar.pack.gz
[2014-05-31 17:23:03.810]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/locale/org-openide-text_ja.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/locale/org-openide-text_ja.jar, in directory: .
[2014-05-31 17:23:03.843]:             [return]: 0
[2014-05-31 17:23:03.843]:         ... command execution finished
[2014-05-31 17:23:03.843]:         deleting file: /usr/local/netbeans-7.4/platform/modules/locale/org-openide-text_ja.jar.pack.gz
[2014-05-31 17:23:03.844]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/locale/org-openide-text_ja.jar
[2014-05-31 17:23:03.844]:         extracting /usr/local/netbeans-7.4/platform/modules/locale/org-openide-text_ru.jar.pack.gz
[2014-05-31 17:23:03.845]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/locale/org-openide-text_ru.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/locale/org-openide-text_ru.jar, in directory: .
[2014-05-31 17:23:03.882]:             [return]: 0
[2014-05-31 17:23:03.882]:         ... command execution finished
[2014-05-31 17:23:03.882]:         deleting file: /usr/local/netbeans-7.4/platform/modules/locale/org-openide-text_ru.jar.pack.gz
[2014-05-31 17:23:03.882]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/locale/org-openide-text_ru.jar
[2014-05-31 17:23:03.882]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-swing-outline.jar.pack.gz
[2014-05-31 17:23:03.884]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-swing-outline.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-swing-outline.jar, in directory: .
[2014-05-31 17:23:03.942]:             [return]: 0
[2014-05-31 17:23:03.942]:         ... command execution finished
[2014-05-31 17:23:03.942]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-swing-outline.jar.pack.gz
[2014-05-31 17:23:03.943]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-swing-outline.jar
[2014-05-31 17:23:03.944]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-lib-uihandler.jar.pack.gz
[2014-05-31 17:23:03.945]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-lib-uihandler.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-lib-uihandler.jar, in directory: .
[2014-05-31 17:23:03.980]:             [return]: 0
[2014-05-31 17:23:03.980]:         ... command execution finished
[2014-05-31 17:23:03.980]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-lib-uihandler.jar.pack.gz
[2014-05-31 17:23:03.980]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-lib-uihandler.jar
[2014-05-31 17:23:03.980]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-modules-print.jar.pack.gz
[2014-05-31 17:23:03.986]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-modules-print.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-modules-print.jar, in directory: .
[2014-05-31 17:23:04.019]:             [return]: 0
[2014-05-31 17:23:04.019]:         ... command execution finished
[2014-05-31 17:23:04.019]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-modules-print.jar.pack.gz
[2014-05-31 17:23:04.019]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-modules-print.jar
[2014-05-31 17:23:04.021]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-core-execution.xml
[2014-05-31 17:23:04.021]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-core-execution.xml
[2014-05-31 17:23:04.024]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-core-multiview.xml
[2014-05-31 17:23:04.025]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-core-multiview.xml
[2014-05-31 17:23:04.025]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-core-multitabs.xml
[2014-05-31 17:23:04.030]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-core-multitabs.xml
[2014-05-31 17:23:04.032]:         extracting /usr/local/netbeans-7.4/platform/config/ModuleAutoDeps/org-openide-explorer.xml
[2014-05-31 17:23:04.033]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/ModuleAutoDeps/org-openide-explorer.xml
[2014-05-31 17:23:04.033]:         extracting /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_pt_BR.jar.pack.gz
[2014-05-31 17:23:04.038]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_pt_BR.jar.pack.gz /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_pt_BR.jar, in directory: .
[2014-05-31 17:23:04.072]:             [return]: 0
[2014-05-31 17:23:04.072]:         ... command execution finished
[2014-05-31 17:23:04.072]:         deleting file: /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_pt_BR.jar.pack.gz
[2014-05-31 17:23:04.072]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_pt_BR.jar
[2014-05-31 17:23:04.073]:         extracting /usr/local/netbeans-7.4/platform/lib/locale/org-openide-modules_ja.jar.pack.gz
[2014-05-31 17:23:04.073]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/lib/locale/org-openide-modules_ja.jar.pack.gz /usr/local/netbeans-7.4/platform/lib/locale/org-openide-modules_ja.jar, in directory: .
[2014-05-31 17:23:04.094]:             [return]: 0
[2014-05-31 17:23:04.095]:         ... command execution finished
[2014-05-31 17:23:04.095]:         deleting file: /usr/local/netbeans-7.4/platform/lib/locale/org-openide-modules_ja.jar.pack.gz
[2014-05-31 17:23:04.095]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/lib/locale/org-openide-modules_ja.jar
[2014-05-31 17:23:04.095]:         extracting /usr/local/netbeans-7.4/platform/lib/locale/org-openide-modules_ru.jar.pack.gz
[2014-05-31 17:23:04.096]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/lib/locale/org-openide-modules_ru.jar.pack.gz /usr/local/netbeans-7.4/platform/lib/locale/org-openide-modules_ru.jar, in directory: .
[2014-05-31 17:23:04.132]:             [return]: 0
[2014-05-31 17:23:04.133]:         ... command execution finished
[2014-05-31 17:23:04.133]:         deleting file: /usr/local/netbeans-7.4/platform/lib/locale/org-openide-modules_ru.jar.pack.gz
[2014-05-31 17:23:04.133]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/lib/locale/org-openide-modules_ru.jar
[2014-05-31 17:23:04.133]:         extracting /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_zh_CN.jar.pack.gz
[2014-05-31 17:23:04.138]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_zh_CN.jar.pack.gz /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_zh_CN.jar, in directory: .
[2014-05-31 17:23:04.171]:             [return]: 0
[2014-05-31 17:23:04.171]:         ... command execution finished
[2014-05-31 17:23:04.171]:         deleting file: /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_zh_CN.jar.pack.gz
[2014-05-31 17:23:04.171]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_zh_CN.jar
[2014-05-31 17:23:04.171]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-netigso.xml
[2014-05-31 17:23:04.177]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-netigso.xml
[2014-05-31 17:23:04.177]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-api-progress.xml
[2014-05-31 17:23:04.177]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-api-progress.xml
[2014-05-31 17:23:04.180]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-startup.xml
[2014-05-31 17:23:04.180]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-startup.xml
[2014-05-31 17:23:04.181]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-windows.xml
[2014-05-31 17:23:04.181]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-windows.xml
[2014-05-31 17:23:04.181]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-network.xml
[2014-05-31 17:23:04.185]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-network.xml
[2014-05-31 17:23:04.190]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-output2.xml
[2014-05-31 17:23:04.190]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-output2.xml
[2014-05-31 17:23:04.193]:         extracting /usr/local/netbeans-7.4/platform/modules/lib/amd64/linux/libjnidispatch-340.so
[2014-05-31 17:23:04.201]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/lib/amd64/linux/libjnidispatch-340.so
[2014-05-31 17:23:04.205]:         extracting /usr/local/netbeans-7.4/platform/modules/locale/org-openide-awt_ja.jar.pack.gz
[2014-05-31 17:23:04.206]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/locale/org-openide-awt_ja.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/locale/org-openide-awt_ja.jar, in directory: .
[2014-05-31 17:23:04.238]:             [return]: 0
[2014-05-31 17:23:04.239]:         ... command execution finished
[2014-05-31 17:23:04.239]:         deleting file: /usr/local/netbeans-7.4/platform/modules/locale/org-openide-awt_ja.jar.pack.gz
[2014-05-31 17:23:04.239]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/locale/org-openide-awt_ja.jar
[2014-05-31 17:23:04.239]:         extracting /usr/local/netbeans-7.4/platform/modules/locale/org-openide-awt_ru.jar.pack.gz
[2014-05-31 17:23:04.240]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/locale/org-openide-awt_ru.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/locale/org-openide-awt_ru.jar, in directory: .
[2014-05-31 17:23:04.277]:             [return]: 0
[2014-05-31 17:23:04.277]:         ... command execution finished
[2014-05-31 17:23:04.277]:         deleting file: /usr/local/netbeans-7.4/platform/modules/locale/org-openide-awt_ru.jar.pack.gz
[2014-05-31 17:23:04.277]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/locale/org-openide-awt_ru.jar
[2014-05-31 17:23:04.278]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-output2.jar.pack.gz
[2014-05-31 17:23:04.280]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-output2.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-output2.jar, in directory: .
[2014-05-31 17:23:04.338]:             [return]: 0
[2014-05-31 17:23:04.338]:         ... command execution finished
[2014-05-31 17:23:04.338]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-output2.jar.pack.gz
[2014-05-31 17:23:04.339]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-output2.jar
[2014-05-31 17:23:04.340]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-windows.jar.pack.gz
[2014-05-31 17:23:04.350]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-windows.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-windows.jar, in directory: .
[2014-05-31 17:23:04.494]:             [return]: 0
[2014-05-31 17:23:04.494]:         ... command execution finished
[2014-05-31 17:23:04.494]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-windows.jar.pack.gz
[2014-05-31 17:23:04.496]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-windows.jar
[2014-05-31 17:23:04.503]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-api-progress.jar.pack.gz
[2014-05-31 17:23:04.503]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-api-progress.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-api-progress.jar, in directory: .
[2014-05-31 17:23:04.538]:             [return]: 0
[2014-05-31 17:23:04.539]:         ... command execution finished
[2014-05-31 17:23:04.539]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-api-progress.jar.pack.gz
[2014-05-31 17:23:04.539]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-api-progress.jar
[2014-05-31 17:23:04.539]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-network.jar.pack.gz
[2014-05-31 17:23:04.540]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-network.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-network.jar, in directory: .
[2014-05-31 17:23:04.575]:             [return]: 0
[2014-05-31 17:23:04.576]:         ... command execution finished
[2014-05-31 17:23:04.576]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-network.jar.pack.gz
[2014-05-31 17:23:04.576]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-network.jar
[2014-05-31 17:23:04.576]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-netigso.jar.pack.gz
[2014-05-31 17:23:04.577]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-netigso.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-netigso.jar, in directory: .
[2014-05-31 17:23:04.615]:             [return]: 0
[2014-05-31 17:23:04.615]:         ... command execution finished
[2014-05-31 17:23:04.615]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-netigso.jar.pack.gz
[2014-05-31 17:23:04.616]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-netigso.jar
[2014-05-31 17:23:04.616]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-print.xml
[2014-05-31 17:23:04.622]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-modules-print.xml
[2014-05-31 17:23:04.622]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-lib-uihandler.xml
[2014-05-31 17:23:04.622]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-lib-uihandler.xml
[2014-05-31 17:23:04.623]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-swing-outline.xml
[2014-05-31 17:23:04.623]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-swing-outline.xml
[2014-05-31 17:23:04.623]:         extracting /usr/local/netbeans-7.4/platform/config/ModuleAutoDeps/org-openide-loaders.xml
[2014-05-31 17:23:04.624]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/ModuleAutoDeps/org-openide-loaders.xml
[2014-05-31 17:23:04.624]:         extracting /usr/local/netbeans-7.4/platform/config/ModuleAutoDeps/org-openide-modules.xml
[2014-05-31 17:23:04.624]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/ModuleAutoDeps/org-openide-modules.xml
[2014-05-31 17:23:04.624]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-libs-testng.xml
[2014-05-31 17:23:04.625]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-libs-testng.xml
[2014-05-31 17:23:04.625]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-libs-jsr223.xml
[2014-05-31 17:23:04.628]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-libs-jsr223.xml
[2014-05-31 17:23:04.635]:         extracting /usr/local/netbeans-7.4/platform/modules/lib/i386/linux/libjnidispatch-340.so
[2014-05-31 17:23:04.638]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/lib/i386/linux/libjnidispatch-340.so
[2014-05-31 17:23:04.644]:         extracting /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_ru.jar.pack.gz
[2014-05-31 17:23:04.644]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_ru.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_ru.jar, in directory: .
[2014-05-31 17:23:04.678]:             [return]: 0
[2014-05-31 17:23:04.678]:         ... command execution finished
[2014-05-31 17:23:04.678]:         deleting file: /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_ru.jar.pack.gz
[2014-05-31 17:23:04.679]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_ru.jar
[2014-05-31 17:23:04.680]:         extracting /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_ja.jar.pack.gz
[2014-05-31 17:23:04.685]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_ja.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_ja.jar, in directory: .
[2014-05-31 17:23:04.718]:             [return]: 0
[2014-05-31 17:23:04.718]:         ... command execution finished
[2014-05-31 17:23:04.718]:         deleting file: /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_ja.jar.pack.gz
[2014-05-31 17:23:04.718]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/locale/org-openide-io_ja.jar
[2014-05-31 17:23:04.720]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-testng.jar.pack.gz
[2014-05-31 17:23:04.721]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-testng.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-testng.jar, in directory: .
[2014-05-31 17:23:04.740]:             [return]: 0
[2014-05-31 17:23:04.740]:         ... command execution finished
[2014-05-31 17:23:04.740]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-testng.jar.pack.gz
[2014-05-31 17:23:04.741]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-testng.jar
[2014-05-31 17:23:04.741]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-jsr223.jar.pack.gz
[2014-05-31 17:23:04.746]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-jsr223.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-jsr223.jar, in directory: .
[2014-05-31 17:23:04.764]:             [return]: 0
[2014-05-31 17:23:04.764]:         ... command execution finished
[2014-05-31 17:23:04.764]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-jsr223.jar.pack.gz
[2014-05-31 17:23:04.764]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-jsr223.jar
[2014-05-31 17:23:04.765]:         extracting /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_pt_BR.jar.pack.gz
[2014-05-31 17:23:04.770]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_pt_BR.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_pt_BR.jar, in directory: .
[2014-05-31 17:23:04.787]:             [return]: 0
[2014-05-31 17:23:04.787]:         ... command execution finished
[2014-05-31 17:23:04.787]:         deleting file: /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_pt_BR.jar.pack.gz
[2014-05-31 17:23:04.788]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_pt_BR.jar
[2014-05-31 17:23:04.788]:         extracting /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_zh_CN.jar.pack.gz
[2014-05-31 17:23:04.788]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_zh_CN.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_zh_CN.jar, in directory: .
[2014-05-31 17:23:04.824]:             [return]: 0
[2014-05-31 17:23:04.824]:         ... command execution finished
[2014-05-31 17:23:04.824]:         deleting file: /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_zh_CN.jar.pack.gz
[2014-05-31 17:23:04.824]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_zh_CN.jar
[2014-05-31 17:23:04.825]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-core-netigso.xml
[2014-05-31 17:23:04.825]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-core-netigso.xml
[2014-05-31 17:23:04.825]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-api-progress.xml
[2014-05-31 17:23:04.830]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-api-progress.xml
[2014-05-31 17:23:04.831]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-core-windows.xml
[2014-05-31 17:23:04.832]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-core-windows.xml
[2014-05-31 17:23:04.832]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-core-network.xml
[2014-05-31 17:23:04.832]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-core-network.xml
[2014-05-31 17:23:04.833]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-core-output2.xml
[2014-05-31 17:23:04.833]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-core-output2.xml
[2014-05-31 17:23:04.833]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-openide-filesystems.xml
[2014-05-31 17:23:04.838]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-openide-filesystems.xml
[2014-05-31 17:23:04.841]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-swing-plaf.xml
[2014-05-31 17:23:04.842]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-swing-plaf.xml
[2014-05-31 17:23:04.846]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-api-search.xml
[2014-05-31 17:23:04.846]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-api-search.xml
[2014-05-31 17:23:04.851]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-openide-util-lookup.xml
[2014-05-31 17:23:04.851]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-openide-util-lookup.xml
[2014-05-31 17:23:04.855]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-io-ui.xml
[2014-05-31 17:23:04.856]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-io-ui.xml
[2014-05-31 17:23:04.858]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-libs-felix.xml
[2014-05-31 17:23:04.860]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-libs-felix.xml
[2014-05-31 17:23:04.861]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-api-visual.xml
[2014-05-31 17:23:04.861]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-api-visual.xml
[2014-05-31 17:23:04.861]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-api-search.jar.pack.gz
[2014-05-31 17:23:04.870]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-api-search.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-api-search.jar, in directory: .
[2014-05-31 17:23:04.949]:             [return]: 0
[2014-05-31 17:23:04.949]:         ... command execution finished
[2014-05-31 17:23:04.949]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-api-search.jar.pack.gz
[2014-05-31 17:23:04.952]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-api-search.jar
[2014-05-31 17:23:04.956]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-felix.jar.pack.gz
[2014-05-31 17:23:04.956]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-felix.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-felix.jar, in directory: .
[2014-05-31 17:23:04.994]:             [return]: 0
[2014-05-31 17:23:04.994]:         ... command execution finished
[2014-05-31 17:23:04.994]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-felix.jar.pack.gz
[2014-05-31 17:23:04.994]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-felix.jar
[2014-05-31 17:23:04.995]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-swing-plaf.jar.pack.gz
[2014-05-31 17:23:04.996]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-swing-plaf.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-swing-plaf.jar, in directory: .
[2014-05-31 17:23:05.033]:             [return]: 0
[2014-05-31 17:23:05.033]:         ... command execution finished
[2014-05-31 17:23:05.033]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-swing-plaf.jar.pack.gz
[2014-05-31 17:23:05.034]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-swing-plaf.jar
[2014-05-31 17:23:05.034]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-io-ui.jar.pack.gz
[2014-05-31 17:23:05.035]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-io-ui.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-io-ui.jar, in directory: .
[2014-05-31 17:23:05.072]:             [return]: 0
[2014-05-31 17:23:05.072]:         ... command execution finished
[2014-05-31 17:23:05.072]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-io-ui.jar.pack.gz
[2014-05-31 17:23:05.073]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-io-ui.jar
[2014-05-31 17:23:05.074]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-api-visual.jar.pack.gz
[2014-05-31 17:23:05.077]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-api-visual.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-api-visual.jar, in directory: .
[2014-05-31 17:23:05.163]:             [return]: 0
[2014-05-31 17:23:05.163]:         ... command execution finished
[2014-05-31 17:23:05.163]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-api-visual.jar.pack.gz
[2014-05-31 17:23:05.164]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-api-visual.jar
[2014-05-31 17:23:05.168]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-libs-testng.xml
[2014-05-31 17:23:05.169]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-libs-testng.xml
[2014-05-31 17:23:05.171]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-libs-jsr223.xml
[2014-05-31 17:23:05.171]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-libs-jsr223.xml
[2014-05-31 17:23:05.175]:         extracting /usr/local/netbeans-7.4/platform/config/ModuleAutoDeps/org-openide-nodes.xml
[2014-05-31 17:23:05.175]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/ModuleAutoDeps/org-openide-nodes.xml
[2014-05-31 17:23:05.179]:         extracting /usr/local/netbeans-7.4/platform/config/ModuleAutoDeps/org-netbeans-core.xml
[2014-05-31 17:23:05.180]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/ModuleAutoDeps/org-netbeans-core.xml
[2014-05-31 17:23:05.183]:         extracting /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_ja.jar.pack.gz
[2014-05-31 17:23:05.184]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_ja.jar.pack.gz /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_ja.jar, in directory: .
[2014-05-31 17:23:05.218]:             [return]: 0
[2014-05-31 17:23:05.218]:         ... command execution finished
[2014-05-31 17:23:05.218]:         deleting file: /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_ja.jar.pack.gz
[2014-05-31 17:23:05.219]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_ja.jar
[2014-05-31 17:23:05.219]:         extracting /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_ru.jar.pack.gz
[2014-05-31 17:23:05.219]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_ru.jar.pack.gz /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_ru.jar, in directory: .
[2014-05-31 17:23:05.256]:             [return]: 0
[2014-05-31 17:23:05.256]:         ... command execution finished
[2014-05-31 17:23:05.256]:         deleting file: /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_ru.jar.pack.gz
[2014-05-31 17:23:05.256]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/lib/locale/org-openide-util_ru.jar
[2014-05-31 17:23:05.257]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-bootstrap.xml
[2014-05-31 17:23:05.257]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-bootstrap.xml
[2014-05-31 17:23:05.257]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-osgi.xml
[2014-05-31 17:23:05.261]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-core-osgi.xml
[2014-05-31 17:23:05.264]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-libs-osgi.xml
[2014-05-31 17:23:05.268]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-libs-osgi.xml
[2014-05-31 17:23:05.271]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-osgi.jar.pack.gz
[2014-05-31 17:23:05.272]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-osgi.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-osgi.jar, in directory: .
[2014-05-31 17:23:05.289]:             [return]: 0
[2014-05-31 17:23:05.289]:         ... command execution finished
[2014-05-31 17:23:05.289]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-osgi.jar.pack.gz
[2014-05-31 17:23:05.290]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-libs-osgi.jar
[2014-05-31 17:23:05.290]:         extracting /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-osgi.jar.pack.gz
[2014-05-31 17:23:05.291]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-osgi.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-osgi.jar, in directory: .
[2014-05-31 17:23:05.327]:             [return]: 0
[2014-05-31 17:23:05.327]:         ... command execution finished
[2014-05-31 17:23:05.327]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-osgi.jar.pack.gz
[2014-05-31 17:23:05.327]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-netbeans-core-osgi.jar
[2014-05-31 17:23:05.328]:         extracting /usr/local/netbeans-7.4/platform/modules/ext/swing-layout-1.0.4.jar.pack.gz
[2014-05-31 17:23:05.329]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/ext/swing-layout-1.0.4.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/ext/swing-layout-1.0.4.jar, in directory: .
[2014-05-31 17:23:05.366]:             [return]: 0
[2014-05-31 17:23:05.366]:         ... command execution finished
[2014-05-31 17:23:05.366]:         deleting file: /usr/local/netbeans-7.4/platform/modules/ext/swing-layout-1.0.4.jar.pack.gz
[2014-05-31 17:23:05.367]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/ext/swing-layout-1.0.4.jar
[2014-05-31 17:23:05.367]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-swing-plaf.xml
[2014-05-31 17:23:05.368]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-swing-plaf.xml
[2014-05-31 17:23:05.368]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-api-search.xml
[2014-05-31 17:23:05.368]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-api-search.xml
[2014-05-31 17:23:05.369]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-core-io-ui.xml
[2014-05-31 17:23:05.369]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-core-io-ui.xml
[2014-05-31 17:23:05.369]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-libs-felix.xml
[2014-05-31 17:23:05.373]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-libs-felix.xml
[2014-05-31 17:23:05.377]:         extracting /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-api-visual.xml
[2014-05-31 17:23:05.378]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/Modules/org-netbeans-api-visual.xml
[2014-05-31 17:23:05.383]:         extracting /usr/local/netbeans-7.4/platform/config/ModuleAutoDeps/org-openide-util.xml
[2014-05-31 17:23:05.383]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/ModuleAutoDeps/org-openide-util.xml
[2014-05-31 17:23:05.387]:         extracting /usr/local/netbeans-7.4/platform/config/ModuleAutoDeps/org-openide-text.xml
[2014-05-31 17:23:05.387]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/config/ModuleAutoDeps/org-openide-text.xml
[2014-05-31 17:23:05.393]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-openide-execution.xml
[2014-05-31 17:23:05.393]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-openide-execution.xml
[2014-05-31 17:23:05.397]:         extracting /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-libs-jna.xml
[2014-05-31 17:23:05.398]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/update_tracking/org-netbeans-libs-jna.xml
[2014-05-31 17:23:05.405]:         extracting /usr/local/netbeans-7.4/platform/modules/org-openide-execution.jar.pack.gz
[2014-05-31 17:23:05.406]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/org-openide-execution.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/org-openide-execution.jar, in directory: .
[2014-05-31 17:23:05.440]:             [return]: 0
[2014-05-31 17:23:05.440]:         ... command execution finished
[2014-05-31 17:23:05.440]:         deleting file: /usr/local/netbeans-7.4/platform/modules/org-openide-execution.jar.pack.gz
[2014-05-31 17:23:05.440]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/org-openide-execution.jar
[2014-05-31 17:23:05.441]:         extracting /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_ru.jar.pack.gz
[2014-05-31 17:23:05.446]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_ru.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_ru.jar, in directory: .
[2014-05-31 17:23:05.480]:             [return]: 0
[2014-05-31 17:23:05.480]:         ... command execution finished
[2014-05-31 17:23:05.480]:         deleting file: /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_ru.jar.pack.gz
[2014-05-31 17:23:05.480]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_ru.jar
[2014-05-31 17:23:05.481]:         extracting /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_ja.jar.pack.gz
[2014-05-31 17:23:05.481]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_ja.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_ja.jar, in directory: .
[2014-05-31 17:23:05.524]:             [return]: 0
[2014-05-31 17:23:05.524]:         ... command execution finished
[2014-05-31 17:23:05.524]:         deleting file: /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_ja.jar.pack.gz
[2014-05-31 17:23:05.524]:         setting permissions 644 on /usr/local/netbeans-7.4/platform/modules/ext/locale/updater_ja.jar
[2014-05-31 17:23:05.529]:         extracting /usr/local/netbeans-7.4/platform/modules/ext/testng-6.8.1-dist.jar.pack.gz
[2014-05-31 17:23:05.534]:         executing command: /usr/local/java/jdk1.7.0_55/jre/bin/unpack200 /usr/local/netbeans-7.4/platform/modules/ext/testng-6.8.1-dist.jar.pack.gz /usr/local/netbeans-7.4/platform/modules/ext/testng-6.8.1-dist.jar, in directory: .
[2014-05-31 17:23:06.066]:             [return]: 134
[2014-05-31 17:23:06.067]:         ... command execution finished
[2014-05-31 17:23:06.069]:         org.netbeans.installer.utils.exceptions.InstallationException: Cannot extract installation data for Base IDE
[2014-05-31 17:23:06.069]:         	at org.netbeans.installer.product.components.Product.install(Product.java:305)
[2014-05-31 17:23:06.069]:         	at org.netbeans.installer.wizard.components.actions.InstallAction.execute(InstallAction.java:155)
[2014-05-31 17:23:06.069]:         	at org.netbeans.installer.wizard.components.WizardAction$1.run(WizardAction.java:123)
[2014-05-31 17:23:06.069]:         Caused by: java.io.IOException: Unpack200 finished with error
[2014-05-31 17:23:06.069]:         Error code: 134
[2014-05-31 17:23:06.069]:         Stdout: 
[2014-05-31 17:23:06.069]:         Stderr: 
[2014-05-31 17:23:06.069]:         	at org.netbeans.installer.utils.FileUtils.unpack(FileUtils.java:1275)
[2014-05-31 17:23:06.069]:         	at org.netbeans.installer.utils.FileUtils.extractByList(FileUtils.java:1831)
[2014-05-31 17:23:06.069]:         	at org.netbeans.installer.utils.FileUtils.extractAll(FileUtils.java:1751)
[2014-05-31 17:23:06.069]:         	at org.netbeans.installer.utils.FileUtils.unjar(FileUtils.java:1102)
[2014-05-31 17:23:06.069]:         	at org.netbeans.installer.product.components.Product.install(Product.java:295)
[2014-05-31 17:23:06.069]:         	... 2 more
[2014-05-31 17:23:06.070]:         NameResolver - to parse Could not install {0}, since the installation of {1} failed
[2014-05-31 17:23:06.070]:         NameResolver - to parse Could not install {0}, since the installation of {1} failed
[2014-05-31 17:23:06.070]:         NameResolver - to parse Canceling, rolling back {0}...
[2014-05-31 17:23:06.074]:         Start rollback of Base IDE(nb-base/7.4.0.0.201310111528)
[2014-05-31 17:23:06.077]:             ... deleting installed files
[2014-05-31 17:23:06.082]:         ... finished rollbacking of Base IDE(nb-base/7.4.0.0.201310111528)
[2014-05-31 17:23:06.082]:         org.netbeans.installer.utils.exceptions.InstallationException: Cannot extract installation data for Base IDE
[2014-05-31 17:23:06.082]:         	at org.netbeans.installer.product.components.Product.install(Product.java:305)
[2014-05-31 17:23:06.082]:         	at org.netbeans.installer.wizard.components.actions.InstallAction.execute(InstallAction.java:155)
[2014-05-31 17:23:06.082]:         	at org.netbeans.installer.wizard.components.WizardAction$1.run(WizardAction.java:123)
[2014-05-31 17:23:06.082]:         Caused by: java.io.IOException: Unpack200 finished with error
[2014-05-31 17:23:06.082]:         Error code: 134
[2014-05-31 17:23:06.082]:         Stdout: 
[2014-05-31 17:23:06.082]:         Stderr: 
[2014-05-31 17:23:06.082]:         	at org.netbeans.installer.utils.FileUtils.unpack(FileUtils.java:1275)
[2014-05-31 17:23:06.082]:         	at org.netbeans.installer.utils.FileUtils.extractByList(FileUtils.java:1831)
[2014-05-31 17:23:06.082]:         	at org.netbeans.installer.utils.FileUtils.extractAll(FileUtils.java:1751)
[2014-05-31 17:23:06.082]:         	at org.netbeans.installer.utils.FileUtils.unjar(FileUtils.java:1102)
[2014-05-31 17:23:06.082]:         	at org.netbeans.installer.product.components.Product.install(Product.java:295)
[2014-05-31 17:23:06.082]:         	... 2 more
[2014-05-31 17:23:06.082]:     ... finished products installation
[2014-05-31 17:23:06.083]:     NameResolver - to parse &Help!
[2014-05-31 17:23:06.083]:     NameResolver - to parse < &Back
[2014-05-31 17:23:06.083]:     NameResolver - to parse &Next >
[2014-05-31 17:23:06.083]:     NameResolver - to parse Cancel
[2014-05-31 17:23:06.084]:     NameResolver - to parse Installation
[2014-05-31 17:23:06.084]:     NameResolver - to parse Installation
[2014-05-31 17:23:06.084]:     NameResolver - to parse Installation
[2014-05-31 17:23:06.084]:     NameResolver - to parse Installation
[2014-05-31 17:23:06.084]:     NameResolver - to parse Please wait while the installer installs NetBeans IDE and runtimes.
[2014-05-31 17:23:06.087]:     NameResolver - to parse Installation
[2014-05-31 17:23:06.088]:     NameResolver - to parse Please wait while the installer installs NetBeans IDE and runtimes.
[2014-05-31 17:23:06.101]:     try temporary directory for sure : 
[2014-05-31 17:23:06.101]:     running headless NetBeans IDE : 
[2014-05-31 17:23:06.105]:     NameResolver - to parse /usr/local/netbeans-7.4
[2014-05-31 17:23:06.105]:         nbLocation = /usr/local/netbeans-7.4
[2014-05-31 17:23:06.110]:         Run [/usr/local/netbeans-7.4/bin/netbeans, , -J-Dnetbeans.close=true, --nosplash, -J-Dorg.netbeans.core.WindowSystem.show=false, -J-Dplugin.manager.install.global=true, --userdir, /tmp/tmpnb]
[2014-05-31 17:23:06.147]:     executing command: /usr/local/netbeans-7.4/bin/netbeans  -J-Dnetbeans.close=true --nosplash -J-Dorg.netbeans.core.WindowSystem.show=false -J-Dplugin.manager.install.global=true --userdir /tmp/tmpnb, in directory: /usr/local/netbeans-7.4
[2014-05-31 17:23:06.156]:             .... exception 
[2014-05-31 17:23:06.156]:         java.io.IOException: Cannot run program "/usr/local/netbeans-7.4/bin/netbeans" (in directory "/usr/local/netbeans-7.4"): error=2, No such file or directory
[2014-05-31 17:23:06.156]:         	at java.lang.ProcessBuilder.start(ProcessBuilder.java:1041)
[2014-05-31 17:23:06.156]:         	at org.netbeans.installer.utils.SystemUtils.executeCommand(SystemUtils.java:238)
[2014-05-31 17:23:06.156]:         	at org.netbeans.installer.wizard.components.sequences.netbeans.NbMainSequence$PopulateCacheAction.runIDE(NbMainSequence.java:489)
[2014-05-31 17:23:06.156]:         	at org.netbeans.installer.wizard.components.sequences.netbeans.NbMainSequence$PopulateCacheAction.execute(NbMainSequence.java:232)
[2014-05-31 17:23:06.156]:         	at org.netbeans.installer.wizard.components.WizardAction$1.run(WizardAction.java:123)
[2014-05-31 17:23:06.156]:         Caused by: java.io.IOException: error=2, No such file or directory
[2014-05-31 17:23:06.156]:         	at java.lang.UNIXProcess.forkAndExec(Native Method)
[2014-05-31 17:23:06.156]:         	at java.lang.UNIXProcess.<init>(UNIXProcess.java:186)
[2014-05-31 17:23:06.156]:         	at java.lang.ProcessImpl.start(ProcessImpl.java:130)
[2014-05-31 17:23:06.156]:         	at java.lang.ProcessBuilder.start(ProcessBuilder.java:1022)
[2014-05-31 17:23:06.156]:         	... 4 more
[2014-05-31 17:23:06.156]:         CleanupNBMsIfLeft(/usr/local/netbeans-7.4)
[2014-05-31 17:23:06.157]:            ... ... done
[2014-05-31 17:23:06.158]:             .... done. 
[2014-05-31 17:23:06.173]:         Checking if java.awt.Desktop.getDesktop().browse() functionality is supported
[2014-05-31 17:23:06.180]:         NameResolver - to parse &Help!
[2014-05-31 17:23:06.181]:         NameResolver - to parse < &Back
[2014-05-31 17:23:06.181]:         NameResolver - to parse &Finish
[2014-05-31 17:23:06.181]:         NameResolver - to parse Cancel
[2014-05-31 17:23:06.181]:         NameResolver - to parse &Finish
[2014-05-31 17:23:06.182]:         NameResolver - to parse text/html
[2014-05-31 17:23:06.184]:         NameResolver - to parse <html><span color="red"><b>Installation of {1} was not completed.</b></span><br><br>Try to run installer again or consult the installation log file for more details:<br>{0}</span></html>
[2014-05-31 17:23:06.190]:         NameResolver - to parse Setup Complete
[2014-05-31 17:23:06.190]:         NameResolver - to parse Setup Complete
[2014-05-31 17:23:06.190]:         NameResolver - to parse Setup Complete
[2014-05-31 17:23:06.190]:         NameResolver - to parse Setup Complete
[2014-05-31 17:23:06.190]:         NameResolver - to parse Click Finish to finish the NetBeans IDE setup.
[2014-05-31 17:23:06.195]:         NameResolver - to parse Setup Complete
[2014-05-31 17:23:06.195]:         NameResolver - to parse Click Finish to finish the NetBeans IDE setup.
[2014-05-31 17:24:21.862]:         entering -- org.netbeans.installer.wizard.components.actions.FinalizeRegistryAction.execute():66
[2014-05-31 17:24:21.863]:         finalizing product registry
[2014-05-31 17:24:21.863]:             ... removing remaining installation data for all the products
[2014-05-31 17:24:21.863]:             deleting file: /root/.nbi/tmp/data,1.jar
[2014-05-31 17:24:21.881]:             deleting file: /root/.nbi/tmp/data,2.jar
[2014-05-31 17:24:21.885]:             deleting file: /root/.nbi/tmp/data,3.jar
[2014-05-31 17:24:21.938]:             deleting file: /root/.nbi/tmp/data,4.jar
[2014-05-31 17:24:21.943]:             deleting file: /root/.nbi/tmp/data,1.jar.0
[2014-05-31 17:24:21.945]:             deleting file: /root/.nbi/tmp/data,2.jar.0
[2014-05-31 17:24:21.946]:             deleting file: /root/.nbi/tmp/data,1.jar.1
[2014-05-31 17:24:21.979]:             deleting file: /root/.nbi/tmp/data,2.jar.1
[2014-05-31 17:24:21.982]:             deleting file: /root/.nbi/tmp/data,3.jar.0
[2014-05-31 17:24:21.986]:             ... save local registry if necessary
[2014-05-31 17:24:21.986]:             ... save registry to file /root/.nbi/registry.xml
[2014-05-31 17:24:21.986]:             entering -- org.netbeans.installer.product.Registry.finalizeRegistry():349
[2014-05-31 17:24:21.986]:             saving product registry file
[2014-05-31 17:24:21.986]:                 ... getting registry document
[2014-05-31 17:24:21.996]:                 ... saving registry document to file /root/.nbi/registry.xml
[2014-05-31 17:24:21.996]:                 entering -- org.netbeans.installer.product.Registry.saveProductRegistry():1017
[2014-05-31 17:24:21.996]:                 saving document to xml file : /root/.nbi/registry.xml
[2014-05-31 17:24:22.273]:                 ... document saved
[2014-05-31 17:24:22.273]:                 exiting -- org.netbeans.installer.product.Registry.saveProductRegistry():1017
[2014-05-31 17:24:22.273]:                 ... saving XML file succesfully finished
[2014-05-31 17:24:22.273]:             ... saving product registry done
[2014-05-31 17:24:22.273]:             exiting -- org.netbeans.installer.product.Registry.finalizeRegistry():349
[2014-05-31 17:24:22.273]:             ... save state file if necessary
[2014-05-31 17:24:22.273]:         finalizing product registry
[2014-05-31 17:24:22.273]:         exiting -- org.netbeans.installer.wizard.components.actions.FinalizeRegistryAction.execute():66
```

I can't figure out what is it. Please help

Thank you.
Indi

---


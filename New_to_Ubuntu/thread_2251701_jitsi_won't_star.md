---
title: "jitsi won't star"
date: 2014-11-06
forum: New to Ubuntu
---

### Post by flex567 on 2014-11-06
A voip software called Jitsi won't star after installation. Do you know what is the problem?

---

### Post by Lars Noodén on 2014-11-06
Which version of jitsi on which version of Ubuntu?  You can also see more information if you launch it via the shell.  Press ctrl-alt-t to bring up a shell and then launch Jitsi in the debug mode:

```

jitsi -d

```

---

### Post by flex567 on 2014-11-06
```
ion: Unresolved constraint in bundle net.java.sip.communicator.replacement.smiley [63]: Unable to resolve 63.0: missing requirement [63.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.smiley [63]: Unable to resolve 63.0: missing requirement [63.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.replacement.vimeo [64] Error starting reference:file:sc-bundles/replacement-vimeo.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.vimeo [64]: Unable to resolve 64.0: missing requirement [64.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.vimeo [64]: Unable to resolve 64.0: missing requirement [64.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.replacement.vbox7 [65] Error starting reference:file:sc-bundles/replacement-vbox7.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.vbox7 [65]: Unable to resolve 65.0: missing requirement [65.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.vbox7 [65]: Unable to resolve 65.0: missing requirement [65.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.replacement.metacafe [66] Error starting reference:file:sc-bundles/replacement-metacafe.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.metacafe [66]: Unable to resolve 66.0: missing requirement [66.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.metacafe [66]: Unable to resolve 66.0: missing requirement [66.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.replacement.flickr [67] Error starting reference:file:sc-bundles/replacement-flickr.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.flickr [67]: Unable to resolve 67.0: missing requirement [67.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.flickr [67]: Unable to resolve 67.0: missing requirement [67.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.replacement.hulu [68] Error starting reference:file:sc-bundles/replacement-hulu.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.hulu [68]: Unable to resolve 68.0: missing requirement [68.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.hulu [68]: Unable to resolve 68.0: missing requirement [68.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.replacement.twitpic [69] Error starting reference:file:sc-bundles/replacement-twitpic.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.twitpic [69]: Unable to resolve 69.0: missing requirement [69.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.twitpic [69]: Unable to resolve 69.0: missing requirement [69.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.replacement.directimage [70] Error starting reference:file:sc-bundles/replacement-directimage.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.directimage [70]: Unable to resolve 70.0: missing requirement [70.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.version) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.directimage [70]: Unable to resolve 70.0: missing requirement [70.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.version) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.replacement.bliptv [71] Error starting reference:file:sc-bundles/replacement-bliptv.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.bliptv [71]: Unable to resolve 71.0: missing requirement [71.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.bliptv [71]: Unable to resolve 71.0: missing requirement [71.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.replacement.viddler [72] Error starting reference:file:sc-bundles/replacement-viddler.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.viddler [72]: Unable to resolve 72.0: missing requirement [72.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.replacement.viddler [72]: Unable to resolve 72.0: missing requirement [72.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.plugin.chatconfig [75] Error starting reference:file:sc-bundles/chatconfig.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.chatconfig [75]: Unable to resolve 75.0: missing requirement [75.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.chatconfig [75]: Unable to resolve 75.0: missing requirement [75.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.plugin.addrbook [76] Error starting reference:file:sc-bundles/addrbook.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.addrbook [76]: Unable to resolve 76.0: missing requirement [76.0] osgi.wiring.package; (osgi.wiring.package=javax.swing))
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.addrbook [76]: Unable to resolve 76.0: missing requirement [76.0] osgi.wiring.package; (osgi.wiring.package=javax.swing)
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.plugin.thunderbird [77] Error starting reference:file:sc-bundles/thunderbook.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.thunderbird [77]: Unable to resolve 77.0: missing requirement [77.0] osgi.wiring.package; (osgi.wiring.package=javax.swing))
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.thunderbird [77]: Unable to resolve 77.0: missing requirement [77.0] osgi.wiring.package; (osgi.wiring.package=javax.swing)
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.plugin.msofficecomm [78] Error starting reference:file:sc-bundles/plugin-msofficecomm.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.msofficecomm [78]: Unable to resolve 78.0: missing requirement [78.0] osgi.wiring.package; (osgi.wiring.package=javax.swing))
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.msofficecomm [78]: Unable to resolve 78.0: missing requirement [78.0] osgi.wiring.package; (osgi.wiring.package=javax.swing)
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.plugin.ldap [79] Error starting reference:file:sc-bundles/plugin-ldap.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.ldap [79]: Unable to resolve 79.0: missing requirement [79.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.contactsource) [caused by: Unable to resolve 111.0: missing requirement [111.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.util) [caused by: Unable to resolve 29.0: missing requirement [29.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.ldap [79]: Unable to resolve 79.0: missing requirement [79.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.contactsource) [caused by: Unable to resolve 111.0: missing requirement [111.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.util) [caused by: Unable to resolve 29.0: missing requirement [29.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.plugin.contactsourceconfig [80] Error starting reference:file:sc-bundles/plugin-contactsourceconfig.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.contactsourceconfig [80]: Unable to resolve 80.0: missing requirement [80.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.contactsource) [caused by: Unable to resolve 111.0: missing requirement [111.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.util) [caused by: Unable to resolve 29.0: missing requirement [29.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.contactsourceconfig [80]: Unable to resolve 80.0: missing requirement [80.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.contactsource) [caused by: Unable to resolve 111.0: missing requirement [111.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.util) [caused by: Unable to resolve 29.0: missing requirement [29.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.plugin.certconfig [81] Error starting reference:file:sc-bundles/plugin-certconfig.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.certconfig [81]: Unable to resolve 81.0: missing requirement [81.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.certificate) [caused by: Unable to resolve 134.0: missing requirement [134.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.gui) [caused by: Unable to resolve 126.0: missing requirement [126.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.resources) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]]])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.certconfig [81]: Unable to resolve 81.0: missing requirement [81.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.certificate) [caused by: Unable to resolve 134.0: missing requirement [134.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.gui) [caused by: Unable to resolve 126.0: missing requirement [126.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.resources) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]]]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.plugin.phonenumbercontactsource [82] Error starting reference:file:sc-bundles/phonenumbercontactsource.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.phonenumbercontactsource [82]: Unable to resolve 82.0: missing requirement [82.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.contactsource) [caused by: Unable to resolve 111.0: missing requirement [111.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.util) [caused by: Unable to resolve 29.0: missing requirement [29.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.phonenumbercontactsource [82]: Unable to resolve 82.0: missing requirement [82.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.contactsource) [caused by: Unable to resolve 111.0: missing requirement [111.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.util) [caused by: Unable to resolve 29.0: missing requirement [29.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.plugin.demuxcontactsource [83] Error starting reference:file:sc-bundles/demuxcontactsource.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.demuxcontactsource [83]: Unable to resolve 83.0: missing requirement [83.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.contactsource) [caused by: Unable to resolve 111.0: missing requirement [111.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.util) [caused by: Unable to resolve 29.0: missing requirement [29.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.demuxcontactsource [83]: Unable to resolve 83.0: missing requirement [83.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.contactsource) [caused by: Unable to resolve 111.0: missing requirement [111.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.util) [caused by: Unable to resolve 29.0: missing requirement [29.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.plugin.propertieseditor [84] Error starting reference:file:sc-bundles/propertieseditor.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.propertieseditor [84]: Unable to resolve 84.0: missing requirement [84.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.propertieseditor [84]: Unable to resolve 84.0: missing requirement [84.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.plugin.securityconfig [17] Error starting reference:file:sc-bundles/securityconfig.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.securityconfig [17]: Unable to resolve 17.0: missing requirement [17.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.securityconfig [17]: Unable to resolve 17.0: missing requirement [17.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.plugin.ippiaccregwizz [18] Error starting reference:file:sc-bundles/ippiaccregwizz.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.ippiaccregwizz [18]: Unable to resolve 18.0: missing requirement [18.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.browserlauncher) [caused by: Unable to resolve 15.0: missing requirement [15.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.util) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.ippiaccregwizz [18]: Unable to resolve 18.0: missing requirement [18.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.browserlauncher) [caused by: Unable to resolve 15.0: missing requirement [15.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.util) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.plugin.iptelaccregwizz [19] Error starting reference:file:sc-bundles/iptelaccregwizz.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.iptelaccregwizz [19]: Unable to resolve 19.0: missing requirement [19.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.browserlauncher) [caused by: Unable to resolve 15.0: missing requirement [15.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.util) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.iptelaccregwizz [19]: Unable to resolve 19.0: missing requirement [19.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.browserlauncher) [caused by: Unable to resolve 15.0: missing requirement [15.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.util) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.plugin.simpleaccreg [4] Error starting reference:file:sc-bundles/simpleaccreg.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.simpleaccreg [4]: Unable to resolve 4.0: missing requirement [4.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.browserlauncher) [caused by: Unable to resolve 15.0: missing requirement [15.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.util) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.plugin.simpleaccreg [4]: Unable to resolve 4.0: missing requirement [4.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.service.browserlauncher) [caused by: Unable to resolve 15.0: missing requirement [15.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.util) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.argdelegation [1] Error starting reference:file:sc-bundles/argdelegation.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.argdelegation [1]: Unable to resolve 1.0: missing requirement [1.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.util) [caused by: Unable to resolve 29.0: missing requirement [29.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.argdelegation [1]: Unable to resolve 1.0: missing requirement [1.0] osgi.wiring.package; (osgi.wiring.package=net.java.sip.communicator.util) [caused by: Unable to resolve 29.0: missing requirement [29.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)
ERROR: Bundle net.java.sip.communicator.shutdowntimeout [36] Error starting reference:file:sc-bundles/shutdown-timeout.jar (org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.shutdowntimeout [36]: Unable to resolve 36.0: missing requirement [36.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)])
org.osgi.framework.BundleException: Unresolved constraint in bundle net.java.sip.communicator.shutdowntimeout [36]: Unable to resolve 36.0: missing requirement [36.0] osgi.wiring.package; (osgi.wiring.package=org.jitsi.service.configuration) [caused by: Unable to resolve 123.0: missing requirement [123.0] osgi.wiring.package; (osgi.wiring.package=javax.imageio)]
    at org.apache.felix.framework.Felix.resolveBundleRevision(Felix.java:3818)
    at org.apache.felix.framework.Felix.startBundle(Felix.java:1868)
    at org.apache.felix.framework.Felix.setActiveStartLevel(Felix.java:1191)
    at org.apache.felix.framework.FrameworkStartLevelImpl.run(FrameworkStartLevelImpl.java:295)
    at java.lang.Thread.run(Thread.java:745)


```

---

### Post by Mike_Walsh on 2014-11-06
Looks like your problem is mainly Java-related. Silly question, perhaps, but....do you have Java installed? Or the Iced Tea equivalent?

Regards,

Mike.

---

### Post by flex567 on 2014-11-06
```
seba@seba-H81-D3:~$ java -version
java version "1.8.0_25"
Java(TM) SE Runtime Environment (build 1.8.0_25-b17)
Java HotSpot(TM) Server VM (build 25.25-b02, mixed mode)


```

---


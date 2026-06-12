---
title: "Building JGraphT 0.7.1 under Ubuntu"
date: 2007-07-21
forum: Programming Talk
---

### Post by Tigera on 2007-07-21
Greetings,

Feisty comes with an older version of JGraphT (0.6.0) and I'd like to use the newer version.  I'm receiving this error.  Does anyone know what I can do to get this to build?  I know that the error is caused by the use of the gnu.xml.transform library, but I can't figure out how to switch implementations.


    [junit] Testcase: testUndirected(org.jgrapht.ext.GraphMLExporterTest):      Caused an ERROR
    [junit] gnu.xml.transform.TransformerFactoryImpl cannot be cast to javax.xml.transform.sax.SAXTransformerFactory
    [junit] java.lang.ClassCastException: gnu.xml.transform.TransformerFactoryImpl cannot be cast to javax.xml.transform.sax.SAXTransformerFactory
    [junit]    at org.jgrapht.ext.GraphMLExporter.export(Unknown Source)
    [junit]    at org.jgrapht.ext.GraphMLExporterTest.testUndirected(GraphMLExporterTest.java:93)



BUILD FAILED
/home/markelba/downloads/jgrapht-0.7.1/build.xml:348: The following error occurred while executing this line:
/home/markelba/downloads/jgrapht-0.7.1/build.xml:331: Test org.jgrapht.ext.GraphMLExporterTest failed

---


---
title: "How to use Jython class from Python?"
date: 2009-09-17
forum: Programming Talk
---

### Post by bostonaholic on 2009-09-17
**I've got a python application and I need to do some XML schema validation using an XSD.**  The easiest way I found to do so was using jython like this:
```
import java.io.File
import javax.xml

class TestJobValidator(object):
    testJobsXml = ""
    testJobsXsd = ""

    def _validate (self):
        schemaFactory = javax.xml.validation.SchemaFactory.newInstance(javax.xml.XMLConstants.W3C_XML_SCHEMA_NS_URI)
        schemaXSD = schemaFactory.newSchema(java.io.File(self.testJobsXsd))
        xsdvalidator = schemaXSD.newValidator()
        parser = javax.xml.parsers.DocumentBuilderFactory.newInstance().newDocumentBuilder()
        document = parser.parse(java.io.File(self.testJobsXml))
        result = xsdvalidator.validate(javax.xml.transform.dom.DOMSource(document)) 
            
        return (result == None)
```
When trying to use this class in my python application, obviously I'll get an import exception because the python interpreter does not know how to handle the java imports used in the jython class.

So right now, I have my python app create a subprocess to run the jython class and I check the returncode of the subprocess like so:
```
    print("START - Jython Subprocess")
    cmd = "jython bin/py/jython/testjobvalidator.jy "+testXml+" "+testXsd
    validation_subprocess = subprocess.Popen(cmd, cwd='.', shell=True)
    validation_subprocess.wait()
    print("FINISHED - Jython Subprocess")

    if not (validation_subprocess.returncode == 0):
        print("\nYour XML did not validate against the provided XSD")
        sys.exit(1)
```
**Is there an easier way to accomplish this other than the way I'm going at it?**

---

### Post by Reiger on 2009-09-17
If your app is (IIRC) C-Python 2.5 compatible you may in fact be able to run the whole thing on the latest Jython and be done with it. :P

You can check that with the latest Jython (or on the site).

Anyways if that is not at all possible; you could invest more time in doing things the Python way and using Python libraries (I am not a python expert by any means and do not know whether or not that is feasible). Alternatively if you really must you can of course try to work with I/O redirection: read output from the Jython process and feed it input from the 'master' process. Make sure to include a special command to kill the Jython process... <_<

---

### Post by bostonaholic on 2009-09-17
> **Reiger said:**
> If your app is (IIRC) C-Python 2.5 compatible you may in fact be able to run the whole thing on the latest Jython and be done with it. :P

You can check that with the latest Jython (or on the site).

I've tried that but thanks.  We're using Python 3.1.  When I tried using the jython interpreter for the entire project, I got import exceptions for things like *configparser*, which I guess is not compatible with the jython interpreter.

> **Reiger said:**
> Anyways if that is not at all possible; you could invest more time in doing things the Python way and using Python libraries (I am not a python expert by any means and do not know whether or not that is feasible). Alternatively if you really must you can of course try to work with I/O redirection: read output from the Jython process and feed it input from the 'master' process.

Trust me, I'd rather use the native python libraries but I haven't yet found an easy way to do xml schema validation this way.  Yes, I could build my own, but for this project that isn't the most efficient solution (too much time to build such a small piece).

> **Reiger said:**
> Make sure to include a special command to kill the Jython process... <_<

I'm not sure if this is needed.  My jython subprocess will exit with a distinct returncode and that is what I check in the python module.  Is there something I'm missing?

---

### Post by Reiger on 2009-09-17
Well currently you are spawning a process per validation which is expensive. If you do the I/O thing you can set up the Jython app so that it listens on input for commands to execute (including terminating itself) and sends out *real output* (e.g. a description of each and every error or a message that everything is ok) which you can then use in your main app.

That ensures you can simply spawn the Jython process once, and then whenever you need it send/retrieve data.

---

### Post by bostonaholic on 2009-09-17
> **Reiger said:**
> Well currently you are spawning a process per validation which is expensive. If you do the I/O thing you can set up the Jython app so that it listens on input for commands to execute (including terminating itself) and sends out *real output* (e.g. a description of each and every error or a message that everything is ok) which you can then use in your main app.

That ensures you can simply spawn the Jython process once, and then whenever you need it send/retrieve data.

Ah ok, I think I know what you're getting at.  Let me explain why I chose to do it this way and maybe defend myself a bit.

This "app" that I'm creating technically isn't really an "application", but more of a set of python scripts that import others and use others for utilities.  So my "app" is actually just a utility script that would not be constantly running.

In more detail, the application (aka set of python scripts) we're building is a test suite to be deployed for use in CI testing.  So spawning this jython subprocess only happens once, when this main application is called from our CI engine (Hudson).

---


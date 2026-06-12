---
title: "python crawler code - what's wrong?"
date: 2007-12-12
forum: Programming Talk
---

### Post by mutenewt on 2007-12-12
I'm in the process of learning python (knowledge remains limited at this point) and recently turned my attention to writing web clients.  I found some source code for a crawler from the book Core Python Programming but can't seem to make it work.  I'm sure I'm missing something obvious but I can't find whats wrong with the code.  Any help would be greatly appreciated.
Thx all!

```
#!/usr/bin/env python

from sys        import argv
from os         import makedirs, unlink
from os.path    import isdir, exists, dirname, splitext
from string     import replace, find, lower
from htmllib    import HTMLParser
from urllib     import urlretrieve
from urlparse   import urlparse, urljoin
from formatter  import DumbWriter, AbstractFormatter
from cStringIO  import StringIO

class Retriever:                 # download Web pages

    def __init__(self, url):
        self.url = url
        self.file = self.filename(url)

    def filename(self, url, deffile='index.htm'):
        parsedurl = urlparse(url, 'http:', 0)  # parse path
        path = parsedurl[1] + parsedurl[2]
        ext = splitext(path)
        if ext[1] == '':
            if newpath[-1] == '/':
                path = path + deffile
            else:
                path = path + '/' + deffile
        dir = dirname(path)
        if not isdir(dir):       # create archive dir if nec.
            if exists(dir): unlink(dir)
            makedirs(dir)
        return path

    def download(self):          # download Web page
        try:
            retval = urllib.urlretrieve(self.url, self.file)
        except IOError:
            retval = ('*** ERROR: invalid URL "%s"' % \
                self.url, )
        return retval

    def parseAndGetLinks(self):  # pars HTML, save links
        self.parser = HTMLParser(AbstractFormatter( \
            DumbWriter(StringIO())))
        self.parser.feed(open(self.file).read())
        self.parser.close()
        return self.parse.anchorlist

class Crawler:                   # manage entire crawling process

    count = 0                    # static downloaded page counter

    def __init__(self, url):
        self.q = [url]
        self.seen = []
        self.dom = urlparse(url)[1]

    def getPage(self, url):
        r = Retriever(url)
        retval = r.download()
        if retval[0] == '*':     # error situation, do not parse
            print retval, '... skipping parse'
            return
        Crawler.count = Crawler.count + 1
        print '\n(', Crawler.count, ')'
        print 'URL:', url
        print 'FILE:', retval[0]
        self.seen.append(url)

        links = r.parseAndGetLinks()  # get and process links
        for eachLink in links:
            if eachLink[:4] != 'http' and \
                    find(eachLink, '://') == -1:
                eachLink = urljoin(url, eachLink)
            print '* ', eachLink,

            if find(lower(eachLink), 'mailto:') != -1:
                print '... discarded, mailto link'
                continue

            if eachLink not in self.seen:
                if find(eachLink, self.dom) == -1:
                    print '... discarded, not in domain'
                else:
                    if eachLink not in self.q:
                        self.q.append(eachLink)
                        print '... new, added to Q'
                    else:
                        print '... discarded, already in Q'
            else:
                    print '... discarded, already processed'

    def go(self):                # process links in queue
        while self.q:
            url = self.q.pop()
            self.getPage(url)

def main():
    if len(argv) > 1:
        url = argv[1]
    else:
        try:
            url = raw_input('Enter starting URL: ')
        except (KeyboardInterrupt, EOFError):
            url = ''

    if not url: return
    robot = Crawler(url)
    robot.go()

if __name__ == '__main__':
    main()

```

---

### Post by Majorix on 2007-12-12
Can you post the error output please? That would help a lot.

---

### Post by Modred on 2007-12-12
Around line 24, what is "newpath"?  It isn't given a value before this line, so trying to find the end of a nonexistent string will fail.
```

    def filename(self, url, deffile='index.htm'):
        parsedurl = urlparse(url, 'http:', 0)  # parse path
        path = parsedurl[1] + parsedurl[2]
        ext = splitext(path)
        if ext[1] == '':
            **if newpath[-1] == '/':**
                path = path + deffile
            else:
                path = path + '/' + deffile

```

I changed "newpath" to "path", and then more problems came up.

Just little typos like after "from urrlib import urlretrieve" they attempt to call "urllib.urlretrieve", which will of course fail because you just imported the function and not the whole module.  So you have a function urlretrieve in your global namespace now, which means you don't need to prepend the urllib module when you call it.

After that, it fails on "self.parse.anchorList", which should be "self.parser.anchorList", considering that self.parser has the parser attached to it.  With this fixed, it appears to run.

If you just mistyped the file, then it was probably a matter of accidental typos.  If the example had all these typos in it and was meant to be a working example, you might want to find better examples, or at least find someone who can help you weed through the mistakes in the ones you find.

---

### Post by pmasiar on 2007-12-12
for more and different training tasks, you may want to check pythonchallenge.com website

---

### Post by mutenewt on 2007-12-13
Thx guys!  It was literally a cut/paste - so no typos were added.  I'll check out the pythonchallenge.  I'm really just trying to find good code samples (shorter the better) that interact with the web - whether that be crawling, file transfers, etc.

Thx again!

---

### Post by pmasiar on 2007-12-13
for code samples, [http://aspn.activestate.com/ASPN/Python/Cookbook/](http://aspn.activestate.com/ASPN/Python/Cookbook/) is one of the best.

---

### Post by dwblas on 2007-12-14
```
if ext[1] == '':
            if newpath[-1] == '/':
                path = path + deffile
            else:
                path = path + '/' + deffile
```Check out os.path.join() to avoid having to do the above.  Also, in any code you should avoid names like "path".  Since that is also a reserved word in Python it can lead to problems, whether you have written the code or not.

---

### Post by Modred on 2007-12-14
> **dwblas said:**
> Also, in any code you should avoid names like "path".  Since that is also a reserved word in Python it can lead to problems, whether you have written the code or not.

'path' is not a [reserved word](http://docs.python.org/ref/keywords.html) in Python, but it is the name of a module.  So it isn't necessarily going to create problems, but it could, depending on how the imports are written.  Anyway, probably a good idea to avoid using it for your own variables anyway.

---


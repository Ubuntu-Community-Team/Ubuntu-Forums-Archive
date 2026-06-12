---
title: "compile poppler"
date: 2010-01-04
forum: Programming Talk
---

### Post by mihaiadrian on 2010-01-04
Does anyone has an idea why poppler 0.12 cannot be compiled on ubuntu 8.04 but it works on ubuntu 8.10 ?

the configure parameters are:
./configure --disable-static   --disable-cairo-output   --enable-xpdf-headers   --disable-poppler-qt   --enable-poppler-qt4   --disable-splash-output   --disable-gdk   --disable-poppler-glib

and the make error on ubuntu 8.04 is:
poppler-page.cc: In static member function &#8216;static Poppler::Link* Poppler::PageData::convertLinkActionToLink(LinkAction*, Poppler::DocumentData*, const QRectF&)&#8217;:
poppler-page.cc:79: warning: enumeration value &#8216;actionRendition&#8217; not handled in switch
poppler-page.cc: In member function &#8216;QImage Poppler::Page::renderToImage(double, double, int, int, int, int, Poppler::Page::Rotation) const&#8217;:
poppler-page.cc:201: warning: unused variable &#8216;rotation&#8217;
poppler-page.cc: In member function &#8216;QImage Poppler::Page::thumbnail() const&#8217;:
poppler-page.cc:293: error: &#8216;Format_RGB888&#8217; is not a member of &#8216;QImage&#8217;
make[3]: *** [poppler-page.lo] Error 1

the code where is error apears is:

QImage Page::thumbnail() const
{
  unsigned char* data = 0;
  int w = 0;
  int h = 0;
  int rowstride = 0;
  GBool r = m_page->page->loadThumb(&data, &w, &h, &rowstride);
  QImage ret;
  if (r)
  {
    // first construct a temporary image with the data got,
    // then force a copy of it so we can free the raw thumbnail data
    ret = QImage(data, w, h, rowstride, QImage::Format_RGB888).copy();
    gfree(data);
  }
  return ret;
}



I've tried more versions and poppler-0.10.7 and below this version works on ubuntu 8.04

Please don't tell me to install it from repository, I need to compile poppler.

---

### Post by Yellow Pasque on 2010-01-04
This is same error, maybe solution will work for you: [http://www.kdenlive.org/forum/qimage-trouble-mlt-revision-1218](http://www.kdenlive.org/forum/qimage-trouble-mlt-revision-1218)

---


---
title: "Pb writing V4L2 driver for MPEG compressed format"
date: 2008-04-24
forum: Programming Talk
---

### Post by Dagonux on 2008-04-24
Hi,


I'm writing a V4L2 driver for a card which capture video in a compressed MPEG4 (H.263+) format.

In the VIDIOC_ENUM_FMT, I return the following structure:

const struct v4l2_fmtdesc tsmpeg4_formats[] = {
   {
       .index          = 0,
       .type           = V4L2_BUF_TYPE_VIDEO_CAPTURE,
       .flags          = V4L2_FMT_FLAG_COMPRESSED,
       .description    = "Hardware-encoded MPEG-4",
       .pixelformat    = V4L2_PIX_FMT_MPEG,
  }
};


But several applications (GStreamer, VLC) display an error "unknown format 1195724877", and close the dialog.

I have the same behavior with the vivi driver.

How do I declare this MPEG4 compressed format in V4L2?

Thanks for your reading,
Dagonux.

---


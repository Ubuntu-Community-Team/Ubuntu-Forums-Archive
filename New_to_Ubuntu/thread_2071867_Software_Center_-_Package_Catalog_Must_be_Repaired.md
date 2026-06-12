---
title: "Software Center - Package Catalog Must be Repaired"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by Mouser58907 on 2012-10-16
I just installed libopencv-dev through the software center. I didn't realize it but I had previously installed OpenCV 2.3 with ROS. I'm not sure if that contributed to the problem. I ran the following commands I've seen from other threads with no luck.

```
sudo apt-get install -f
```
gives
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libopencv-calib3d2.3 libopencv-contrib2.3 libopencv-core-dev libopencv-core2.3 libopencv-features2d2.3 libopencv-flann2.3 libopencv-gpu2.3 libopencv-highgui2.3 libopencv-imgproc2.3
  libopencv-legacy2.3 libopencv-ml2.3 libopencv-objdetect2.3 libopencv-video2.3
The following NEW packages will be installed:
  libopencv-calib3d2.3 libopencv-contrib2.3 libopencv-core-dev libopencv-core2.3 libopencv-features2d2.3 libopencv-flann2.3 libopencv-gpu2.3 libopencv-highgui2.3 libopencv-imgproc2.3
  libopencv-legacy2.3 libopencv-ml2.3 lCorrecting dependencies... Doneibopencv-objdetect2.3 libopencv-video2.3
0 upgraded, 13 newly installed, 0 to remove and 7 not upgraded.
12 not fully installed or removed.
Need to get 0 B/6,714 kB of archives.
After this operation, 32.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 319494 files and directories currently installed.)
Unpacking libopencv-core2.3 (from .../libopencv-core2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-core2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_core.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
dpkg-deb: error: subprocess paste was killedReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libopencv-calib3d2.3 libopencv-contrib2.3 libopencv-core-dev libopencv-core2.3 libopencv-features2d2.3 libopencv-flann2.3 libopencv-gpu2.3 libopencv-highgui2.3 libopencv-imgproc2.3
  libopencv-legacy2.3 libopencv-ml2.3 libopencv-objdetect2.3 libopencv-video2.3
The following NEW packages will be installed:
  libopencv-calib3d2.3 libopencv-contrib2.3 libopencv-core-dev libopencv-core2.3 libopencv-features2d2.3 libopencv-flann2.3 libopencv-gpu2.3 libopencv-highgui2.3 libopencv-imgproc2.3
  libopencv-legacy2.3 libopencv-ml2.3 libopencv-objdetect2.3 libopencv-video2.3
0 upgraded, 13 newly installed, 0 to remove and 7 not upgraded.
12 not fully installed or removed.
Need to get 0 B/6,714 kB of archives.
After this operation, 32.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 319494 files and directories currently installed.)
Unpacking libopencv-core2.3 (from .../libopencv-core2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-core2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_core.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-flann2.3 (from .../libopencv-flann2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-flann2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_flann.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-imgproc2.3 (from .../libopencv-imgproc2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-imgproc2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_imgproc.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-highgui2.3 (from .../libopencv-highgui2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-highgui2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_highgui.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-features2d2.3 (from .../libopencv-features2d2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-features2d2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_features2d.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-calib3d2.3 (from .../libopencv-calib3d2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-calib3d2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_calib3d.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-gpu2.3 (from .../libopencv-gpu2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-gpu2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_gpu.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              Unpacking libopencv-ml2.3 (from .../libopencv-ml2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-ml2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_ml.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-objdetect2.3 (from .../libopencv-objdetect2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-objdetect2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_objdetect.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-core-dev (from .../libopencv-core-dev_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-core-dev_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/opencv_stitching', which is also in package libopencv2.3-bin 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-contrib2.3 (from .../libopencv-contrib2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-contrib2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_contrib.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-video2.3 (from .../libopencv-video2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-video2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_video.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libopencv-calib3d2.3 libopencv-contrib2.3 libopencv-core-dev libopencv-core2.3 libopencv-features2d2.3 libopencv-flann2.3 libopencv-gpu2.3 libopencv-highgui2.3 libopencv-imgproc2.3
  libopencv-legacy2.3 libopencv-ml2.3 libopencv-objdetect2.3 libopencv-video2.3
The following NEW packages will be installed:
  libopencv-calib3d2.3 libopencv-contrib2.3 libopencv-core-dev libopencv-core2.3 libopencv-features2d2.3 libopencv-flann2.3 libopencv-gpu2.3 libopencv-highgui2.3 libopencv-imgproc2.3
  libopencv-legacy2.3 libopencv-ml2.3 libopencv-objdetect2.3 libopencv-video2.3
0 upgraded, 13 newly installed, 0 to remove and 7 not upgraded.
12 not fully installed or removed.
Need to get 0 B/6,714 kB of archives.
After this operation, 32.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 319494 files and directories currently installed.)
Unpacking libopencv-core2.3 (from .../libopencv-core2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-core2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_core.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-flann2.3 (from .../libopencv-flann2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-flann2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_flann.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-imgproc2.3 (from .../libopencv-imgproc2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-imgproc2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_imgproc.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-highgui2.3 (from .../libopencv-highgui2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-highgui2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_highgui.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-features2d2.3 (from .../libopencv-features2d2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-features2d2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_features2d.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-calib3d2.3 (from .../libopencv-calib3d2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-calib3d2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_calib3d.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-gpu2.3 (from .../libopencv-gpu2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-gpu2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_gpu.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              Unpacking libopencv-ml2.3 (from .../libopencv-ml2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-ml2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_ml.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-objdetect2.3 (from .../libopencv-objdetect2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-objdetect2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_objdetect.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-core-dev (from .../libopencv-core-dev_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-core-dev_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/opencv_stitching', which is also in package libopencv2.3-bin 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-contrib2.3 (from .../libopencv-contrib2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-contrib2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_contrib.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-video2.3 (from .../libopencv-video2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-video2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_video.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-legacy2.3 (from .../libopencv-legacy2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-legacy2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_legacy.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libopencv-core2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-flann2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-imgproc2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-highgui2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-features2d2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-calib3d2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-gpu2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-ml2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-objdetect2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-core-dev_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-contrib2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-video2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-legacy2.3_2.3.1-7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-legacy2.3 (from .../libopencv-legacy2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-legacy2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_legacy.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libopencv-core2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-flann2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-imgproc2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-highgui2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-features2d2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-calib3d2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-gpu2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-ml2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-objdetect2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-core-dev_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-contrib2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-video2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-legacy2.3_2.3.1-7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) by signal (Broken pipe)
Unpacking libopencv-flann2.3 (from .../libopencv-flann2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-flann2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_flann.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-imgproc2.3 (from .../libopencv-imgproc2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-imgproc2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_imgproc.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-highgui2.3 (from .../libopencv-highgui2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-highgui2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_highgui.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-features2d2.3 (from .../libopencv-features2d2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-features2d2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_features2d.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-calib3d2.3 (from .../libopencv-calib3d2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-calib3d2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_calib3d.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-gpu2.3 (from .../libopencv-gpu2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-gpu2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_gpu.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              Unpacking libopencv-ml2.3 (from .../libopencv-ml2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-ml2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_ml.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-objdetect2.3 (from .../libopencv-objdetect2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-objdetect2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_objdetect.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-core-dev (from .../libopencv-core-dev_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-core-dev_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/opencv_stitching', which is also in package libopencv2.3-bin 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-contrib2.3 (from .../libopencv-contrib2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-contrib2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_contrib.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-video2.3 (from .../libopencv-video2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-video2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_video.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libopencv-legacy2.3 (from .../libopencv-legacy2.3_2.3.1-7_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencv-legacy2.3_2.3.1-7_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencv_legacy.so.2.3.1', which is also in package libopencv2.3 2.3.1+svn6514+branch23-12~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libopencv-core2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-flann2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-imgproc2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-highgui2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-features2d2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-calib3d2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-gpu2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-ml2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-objdetect2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-core-dev_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-contrib2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-video2.3_2.3.1-7_amd64.deb
 /var/cache/apt/archives/libopencv-legacy2.3_2.3.1-7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

and
```
sudo dpkg --configure -a
```
gives
```
craig@ubuntu:~/Desktop/labs/Lab_1_OpenCV$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libopencv-objdetect-dev:
 libopencv-objdetect-dev depends on libopencv-objdetect2.3 (= 2.3.1-7); however:
  Package libopencv-objdetect2.3 is not installed.
dpkg: error processing libopencv-objdetect-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-video-dev:
 libopencv-video-dev depends on libopencv-video2.3 (= 2.3.1-7); however:
  Package libopencv-video2.3 is not installed.
dpkg: error processing libopencv-video-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-ml-dev:
 libopencv-ml-dev depends on libopencv-core-dev (= 2.3.1-7); however:
  Package libopencv-core-dev is not installed.
 libopencv-ml-dev depends on libopencv-ml2.3 (= 2.3.1-7); however:
  Package libopencv-ml2.3 is not installed.
dpkg: error processing libopencv-ml-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-highgui-dev:
 libopencv-highgui-dev depends on libopencv-highgui2.3 (= 2.3.1-7); however:
  Package libopencv-highgui2.3 is not installed.
dpkg: error processing libopencv-highgui-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-contrib-dev:
 libopencv-contrib-dev depends on libopencv-contrib2.3 (= 2.3.1-7); however:
  Package libopencv-contrib2.3 is not installed.
dpkg: error processing libopencv-contrib-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-calib3d-dev:
 libopencv-calib3d-dev depends on libopencv-calib3d2.3 (= 2.3.1-7); however:
  Package libopencv-calib3d2.3 is not installed.
dpkg: error processing libopencv-calib3d-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-imgproc-dev:
 libopencv-imgproc-dev depends on libopencv-core-dev (= 2.3.1-7); however:
  Package libopencv-core-dev is not installed.
 libopencv-imgproc-dev depends on libopencv-imgproc2.3 (= 2.3.1-7); however:
  Package libopencv-imgproc2.3 is not installed.
dpkg: error processing libopencv-imgproc-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-gpu-dev:
 libopencv-gpu-dev depends on libopencv-core-dev (= 2.3.1-7); however:
  Package libopencv-core-dev is not installed.
 libopencv-gpu-dev depends on libopencv-gpu2.3 (= 2.3.1-7); however:
  Package libopencv-gpu2.3 is not installed.
dpkg: error processing libopencv-gpu-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-dev:
 libopencv-dev depends on libopencv-core-dev (= 2.3.1-7); however:
  Package libopencv-core-dev is not installed.
 libopencv-dev depends on libopencv-ml-dev (= 2.3.1-7); however:
  Package libopencv-ml-dev is not configured yet.
 libopencv-dev depends on libopencv-imgproc-dev (= 2.3.1-7); however:
  Package libopencv-imgproc-dev is not configured yet.
 libopencv-dev depends on libopencv-video-dev (= 2.3.1-7); however:
  Package libopencv-video-dev is not configured yet.
 libopencv-dev depends on libopencv-objdetect-dev (= 2.3.1-7); however:
  Package libopencv-objdetect-dev is not configured yet.
 libopencv-dev depends on libopencv-gpu-dev (= 2.3.1-7); however:
  Package libopencv-gpu-dev is not configured yet.
 libopencv-dev depends on libopencv-highgui-dev (= 2.3.1-7); however:
  Package libopencv-highgui-dev is not configured yet.
 libopencv-dev depends on libopencv-calib3d-dev (= 2.3.1-7); however:
  Package libopencv-calib3d-dev is not configured yet.
 libopencv-dev depends on libopencv-contrib-dev (= 2.3.1-7); however:
  Package libopencv-contrib-dev is not configured yet.
dpkg: error processing libopencv-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-features2d-dev:
 libopencv-features2d-dev depends on libopencv-highgui-dev (= 2.3.1-7); however:
  Package libopencv-highgui-dev is not configured yet.
 libopencv-features2d-dev depends on libopencv-features2d2.3 (= 2.3.1-7); however:
  Package libopencv-features2d2.3 is not installed.
dpkg: error processing libopencv-features2d-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-legacy-dev:
 libopencv-legacy-dev depends on libopencv-video-dev (= 2.3.1-7); however:
  Package libopencv-video-dev is not configured yet.
 libopencv-legacy-dev depends on libopencv-calib3d-dev (= 2.3.1-7); however:
  Package libopencv-calib3d-dev is not configured yet.
 libopencv-legacy-dev depends on libopencv-legacy2.3 (= 2.3.1-7); however:
  Package libopencv-legacy2.3 is not installed.
dpkg: error processing libopencv-legacy-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencv-flann-dev:
 libopencv-flann-dev depends on libopencv-core-dev (= 2.3.1-7); however:
  Package libopencv-core-dev is not installed.
 libopencv-flann-dev depends on libopencv-flann2.3 (= 2.3.1-7); however:
  Package libopencv-flann2.3 is not installed.
dpkg: error processing libopencv-flann-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libopencv-objdetect-dev
 libopencv-video-dev
 libopencv-ml-dev
 libopencv-highgui-dev
 libopencv-contrib-dev
 libopencv-calib3d-dev
 libopencv-imgproc-dev
 libopencv-gpu-dev
 libopencv-dev
 libopencv-features2d-dev
 libopencv-legacy-dev
 libopencv-flann-dev
```

Thanks for your help.

---

### Post by Bashing-om on 2012-10-16
Mouser58907; Hi !

How about removing both packages;
You can remove a package and all of its now-no-longer-needed dependencies in one step:

Termianl command:
```
 sudo apt-get remove --auto-remove <package_name>
```If all looks well, re-install the package of choice.
[INDENT]hth <==BDQ

[/INDENT]

---

### Post by Mouser58907 on 2012-10-16
Hi, I solved this problem by manually deleting all of the OpenCV Libs and then running this command.

```
sudo dpkg -r libopencv*
```

---

### Post by Bashing-om on 2012-10-16
Good! Glad ya got it resolved.
please mark this thread as solved in the thread tools.

What works, works ! <==BDQ

---


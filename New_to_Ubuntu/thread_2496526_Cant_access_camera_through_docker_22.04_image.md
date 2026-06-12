---
title: "Cant access camera through docker 22.04 image"
date: 2024-04-01
forum: New to Ubuntu
---

### Post by excadigger on 2024-04-01
I have a raspberry pi5 with the default OS. I could not run ROS2 humble on it so I have a docker container with ubuntu 22.04. Humble runs on it and I have gotten Lidar data to my laptop after some trial and error. The last piece of the puzzle is to get video, so I have bought a pi camera and it works without the docker container. Whenever I use the docker container though, I get the following:

root@Andy:/home/pi/libcamera# libcamera-hello -v
[0:16:16.801743727] [685]  INFO Camera camera_manager.cpp:284 libcamera v0.2.0+46-075b54d5
Options:
    verbose: 2
    info_text:#%frame (%fps fps) exp %exp ag %ag dg %dg
    timeout: 5000ms
    width: 0
    height: 0
    output: 
    post_process_file: 
    preview: default
    qt-preview: 0
    transform: identity
    roi: all
    metering: centre
    exposure: normal
    ev: 0
    awb: auto
    flush: false
    wrap: 0
    brightness: 0
    contrast: 1
    saturation: 1
    sharpness: 1
    framerate: 30
    denoise: auto
    viewfinder-width: 0
    viewfinder-height: 0
    tuning-file: (libcamera)
    lores-width: 0
    lores-height: 0
    autofocus-range: normal
    autofocus-speed: normal
    autofocus-window: all
    hdr: off
    mode: unspecified
    viewfinder-mode: unspecified
    metadata: 
    metadata-format: json
Preview window unavailable
Running without preview window
Opening camera...
Closing RPiCam application(frames displayed 0, dropped 0)
Camera stopped!
Tearing down requests, buffers and configuration
Camera closed
ERROR: *** no cameras available ***

I have tried to run with privilege, mount the whole dev onto the container and change the cgroup:

docker run -it --rm --privileged \
  --device-cgroup-rule='c 81:* rwm' \
  --net=host \
  -v /dev:/dev \
  my_ros_image

I cant find anything online that helps. So does anyone know? Or have a smart way of bypassing the problem? I am able to stream from the pi5 to my laptop, and then create a ros node there, but there is like a 3 second lag when I use 540 x 720 and that wont work for a real time robot.

---

### Post by dives44 on 2024-12-06
Hi,
I'm having the exact same issue.
I can interact with the camera in the host, but get the "[FONT=&quot]ERROR: *** no cameras available ***" message in docker.
[/FONT]
Did you had any luck with that ?

---


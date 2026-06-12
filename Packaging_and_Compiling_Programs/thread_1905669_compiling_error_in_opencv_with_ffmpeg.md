---
title: "compiling error in opencv with ffmpeg"
date: 2012-01-07
forum: Packaging and Compiling Programs
---

### Post by matrronchi on 2012-01-07
I don't know if I posted in the right place, I tried also in theProgramming Talk section, sorry if I made a mistake.

I am trying to install the library Open-CV working on on Ubuntu 11.04.

I followed all instructions found in the [InstallationGuide][1].

However after installing with success I realized that I hadn't `FFMPEG`  support because in my configuration file `FFMPEG` was disabled:

    Video I/O: 
    --     DC1394 1.x:                 NO 
    --     DC1394 2.x:                 YES 
    --     FFMPEG:                     NO 
    --       codec:                    YES 
    --       format:                   YES 
    --       util:                     YES 
    --       swscale:                  NO 
    --       gentoo-style:             YES 
    --     GStreamer:                  YES 
    --     UniCap:                     NO 
    --     PvAPI:                      NO 
    --     V4L/V4L2:                   Using libv4l 
    --     Xine:                       NO

 
So I tried to rebuild everything after installing FFMEPG as decribed [here][2].

After configuring installation with the instruction

    cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D BUILD_PYTHON_SUPPORT=ON ../OpenCV-2.3.1

I ran the make command getting this error:

    make[2]: *** [bin/opencv_test_calib3d] Error 1
    make[1]: *** [modules/calib3d/CMakeFiles/opencv_test_calib3d.dir/all] Error 2
    make: *** [all] Error 2

This is the point of compilation where the error is coming out:

    Linking CXX executable ../../bin/opencv_test_calib3d
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_analysis_headerout'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_set_out_samplerate'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_set_disable_reservoir'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_encode_buffer'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vaUnmapBuffer'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vaDestroyBuffer'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `th_comment_clear'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `x264_param_default'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `x264_param_apply_profile'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_set_brate'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `x264_encoder_headers'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `faacEncGetCurrentConfiguration'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_analysis_blockout'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_info_clear'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_analysis_buffer'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `th_comment_init'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vaCreateBuffer'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_set_bWriteVbrTag'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `faacEncSetConfiguration'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `th_encode_ctl'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `D_IF_decode'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `faacEncGetDecoderSpecificInfo'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_block_clear'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_close'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `x264_encoder_encode'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_set_VBR'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `Encoder_Interface_init'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_analysis'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_get_framesize'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `faacEncOpen'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_init'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `th_encode_packetout'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_set_quality'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `Decoder_Interface_exit'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `th_encode_alloc'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_encode_setup_vbr'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `th_info_clear'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_set_in_samplerate'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `x264_encoder_reconfig'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `x264_param_apply_fastfirstpass'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_set_VBR_quality'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_set_mode'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `D_IF_init'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_set_num_channels'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `faacEncEncode'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_encode_setup_managed'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `Encoder_Interface_exit'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `Decoder_Interface_init'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vaRenderPicture'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_encode_ctl'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `th_info_init'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_analysis_init'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `x264_encoder_delayed_frames'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `x264_param_parse'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `th_encode_free'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `D_IF_exit'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_dsp_clear'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `Decoder_Interface_Decode'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vaMapBuffer'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_block_init'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `x264_bit_depth'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `x264_picture_init'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `x264_encoder_close'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `x264_encoder_open_120'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `faacEncClose'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vaEndPicture'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_encode_flush'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_encode_buffer_interleaved'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_comment_init'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_comment_clear'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_init_params'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `x264_param_default_preset'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_encode_setup_init'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_bitrate_addblock'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_comment_add_tag'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `th_encode_flushheader'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `lame_encode_buffer_int'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `th_encode_ycbcr_in'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_bitrate_flushpacket'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_analysis_wrote'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vorbis_info_init'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `Encoder_Interface_Encode'
    ../../lib/libopencv_highgui.so.2.3.1: undefined reference to `vaBeginPicture'
    collect2: ld returned 1 exit status

can anybody please tell me what's the problem with installation process I'm following?

Why is there this library referentiation error?

[1]: [http://opencv.willowgarage.com/wiki/InstallGuide_Linux](http://opencv.willowgarage.com/wiki/InstallGuide_Linux)
[2]: [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---


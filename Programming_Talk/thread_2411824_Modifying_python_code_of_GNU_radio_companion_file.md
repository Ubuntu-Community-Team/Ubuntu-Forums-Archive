---
title: "Modifying python code of GNU radio companion file"
date: 2019-02-04
forum: Programming Talk
---

### Post by rensisam on 2019-02-04
**I have created a simple grc with source->throttle ->FFT sink/File sink**


**the corresponding python file is:-**

[FONT=courier new]#!/usr/bin/env python2
# -*- coding: utf-8 -*-
##################################################
# GNU Radio Python Flow Graph
# Title: Rsm 01 02 2019
# Generated: Fri Feb  1 16:54:42 2019
##################################################

if __name__ == '__main__':
    import ctypes
    import sys
    if sys.platform.startswith('linux'):
        try:
            x11 = ctypes.cdll.LoadLibrary('libX11.so')
            x11.XInitThreads()
        except:
            print "Warning: failed to XInitThreads()"

from gnuradio import analog
from gnuradio import blocks
from gnuradio import eng_notation
from gnuradio import gr
from gnuradio import wxgui
from gnuradio.eng_option import eng_option
from gnuradio.fft import window
from gnuradio.filter import firdes
from gnuradio.wxgui import fftsink2
from grc_gnuradio import wxgui as grc_wxgui
from optparse import OptionParser
import wx


class RSM_01_02_2019(grc_wxgui.top_block_gui):

    def __init__(self):
        grc_wxgui.top_block_gui.__init__(self, title="Rsm 01 02 2019")
        _icon_path = "/usr/share/icons/hicolor/32x32/apps/gnuradio-grc.png"
        self.SetIcon(wx.Icon(_icon_path, wx.BITMAP_TYPE_ANY))

        ##################################################
        # Variables
        ##################################################
        self.samp_rate = samp_rate = 32000

        ##################################################
        # Blocks
        ##################################################
        self.wxgui_fftsink2_0 = fftsink2.fft_sink_c(
            self.GetWin(),
            baseband_freq=0,
            y_per_div=10,
            y_divs=10,
            ref_level=0,
            ref_scale=2.0,
            sample_rate=samp_rate,
            fft_size=1024,
            fft_rate=15,
            average=False,
            avg_alpha=None,
            title="FFT Plot",
            peak_hold=False,
        )
        self.Add(self.wxgui_fftsink2_0.win)
        self.blocks_throttle_0 = blocks.throttle(gr.sizeof_gr_complex*1, samp_rate,True)
        self.blocks_file_sink_0 = blocks.file_sink(gr.sizeof_gr_complex*1, "RSM.bin", False)
        self.blocks_file_sink_0.set_unbuffered(False)
        self.analog_sig_source_x_0 = analog.sig_source_c(samp_rate, analog.GR_COS_WAVE, 1000, 1, 0)

        ##################################################
        # Connections
        ##################################################
        self.connect((self.analog_sig_source_x_0, 0), (self.blocks_throttle_0, 0))    
        self.connect((self.blocks_throttle_0, 0), (self.blocks_file_sink_0, 0))    
        self.connect((self.blocks_throttle_0, 0), (self.wxgui_fftsink2_0, 0))    

    def get_samp_rate(self):
        return self.samp_rate

    def set_samp_rate(self, samp_rate):
        self.samp_rate = samp_rate
        self.analog_sig_source_x_0.set_sampling_freq(self.samp_rate)
        self.wxgui_fftsink2_0.set_sample_rate(self.samp_rate)
        self.blocks_throttle_0.set_sample_rate(self.samp_rate)




def main(top_block_cls=RSM_01_02_2019, options=None):

    tb = top_block_cls()
   
    
    tb.Start(True)
    tb.Wait()


if __name__ == '__main__':
    try:
        RSM_01_02_2019().run()
    except [[KeyboardInterrupt]]:
        pass[/FONT]

[B]Now I want to modify the python file to find the square of the signal value and pribnt it.

How can I do it?

Kindly help
Rensi[/B]

---

### Post by howefield on 2019-02-04
Thread moved to the "*Programming Talk*" forum, probably a better fit.

---


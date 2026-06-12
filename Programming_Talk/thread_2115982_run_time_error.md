---
title: "run time error"
date: 2013-02-14
forum: Programming Talk
---

### Post by nycap on 2013-02-14
using ubuntu 12.10 i am trying to run a python block, namely OP25, in GNU Radio Companion v3.6.3-35-g4435082f.   i get the following error:

```
Executing: "/home/matt/op25_grc.py"

Imported legacy fsk4
Using Volk machine: ssse3_32
Traceback (most recent call last):
  File "/home/matt/op25_grc.py", line 493, in <module>
    tb = op25_grc()
  File "/home/matt/op25_grc.py", line 231, in __init__
    self.wxgui_fftsink2_0_0.set_callback(wxgui_fftsink2_0_0_callback)
  File "/usr/local/lib/python2.7/dist-packages/gnuradio/gr/hier_block2.py", line 54, in __getattr__
    return getattr(self._hb, name)
AttributeError: 'gr_hier_block2_sptr' object has no attribute 'set_callback'
```i cannot find any sort of solution on the web anywhere.  any sort of help will be much appreciated. thanks in advance.

---

### Post by r-senior on 2013-02-14
Do either of these threads help?

Sounds like a version problem?

[https://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CDQQFjAA&url=https%3A%2F%2Fgithub.com%2Ftitanous%2Fhomebrew-gnuradio%2Fissues%2F9&ei=DCkdUYOqG-HV0QX_7IDwBQ&usg=AFQjCNEdNZxWvH0PUBgzDeFNqFT8Ksz34w&sig2=vSvNDW3pnTSUUbK4x4XJLQ&bvm=bv.42452523,d.d2k](https://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CDQQFjAA&url=https%3A%2F%2Fgithub.com%2Ftitanous%2Fhomebrew-gnuradio%2Fissues%2F9&ei=DCkdUYOqG-HV0QX_7IDwBQ&usg=AFQjCNEdNZxWvH0PUBgzDeFNqFT8Ksz34w&sig2=vSvNDW3pnTSUUbK4x4XJLQ&bvm=bv.42452523,d.d2k)

[https://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&cad=rja&ved=0CEQQFjAC&url=http%3A%2F%2Fwww.ruby-forum.com%2Ftopic%2F4402908&ei=DCkdUYOqG-HV0QX_7IDwBQ&usg=AFQjCNFPg7c2RbFn_U0iT2b1YadW3LJqeA&sig2=rGMfex2wQk7yq2groeCBnQ&bvm=bv.42452523,d.d2k](https://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&cad=rja&ved=0CEQQFjAC&url=http%3A%2F%2Fwww.ruby-forum.com%2Ftopic%2F4402908&ei=DCkdUYOqG-HV0QX_7IDwBQ&usg=AFQjCNFPg7c2RbFn_U0iT2b1YadW3LJqeA&sig2=rGMfex2wQk7yq2groeCBnQ&bvm=bv.42452523,d.d2k)

---

### Post by nycap on 2013-02-15
yes i looked at all those threads.  but i have the latest version of the program.  and others that said they updated said that it was not a solution.

         I am using ubuntu 12.10 and python version 2.7.3. i run the following          command in terminal:
```
matt@matt-Inspiron-1525:~$ python -m          trace --count -C . op25_grc.py
```

Here is the output with an          error:
```
Imported legacy fsk4
Using Volk machine: ssse3_32
Traceback          (most recent call last):
File "/usr/lib/python2.7/runpy.py", line          162, in _run_module_as_main
"__main__", fname, loader, pkg_name)
File          "/usr/lib/python2.7/runpy.py", line 72, in _run_code
exec          code in run_globals
File "/usr/lib/python2.7/trace.py", line 819,          in <module>
main()
File "/usr/lib/python2.7/trace.py",          line 807, in main
t.runctx(code, globs, globs)
File          "/usr/lib/python2.7/trace.py", line 513, in runctx
exec          cmd in globals, locals
File "op25_grc.py", line 493, in <module>
tb          = op25_grc()
File "op25_grc.py", line 231, in __init__
self.wxgui_fftsink2_0_0.set_callback(wxgui_fftsink2_0_0_callback)
File          "/usr/local/lib/python2.7/dist-packages/gnuradio/gr/hier_block2.py",          line 54, in __getattr__
return getattr(self._hb, name)
AttributeError:          'gr_hier_block2_sptr' object has no attribute 'set_callback'
```

      
                here is the code for "hier_block2_.py":
```
#          Copyright 2006,2007 Free Software Foundation, Inc.
#
# This file          is part of GNU Radio
#
# GNU Radio is free software; you can          redistribute it and/or modify
# it under the terms of the GNU          General Public License as published by
# the Free Software          Foundation; either version 3, or (at your option)
# any later          version.
#
# GNU Radio is distributed in the hope that it will          be useful,
# but WITHOUT ANY WARRANTY; without even the implied          warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.          See the
# GNU General Public License for more details.
#
#          You should have received a copy of the GNU General Public License
#          along with GNU Radio; see the file COPYING. If not, write to
# the          Free Software Foundation, Inc., 51 Franklin Street,
# Boston, MA          02110-1301, USA.
#

from gnuradio_core import hier_block2_swig
try:
import          pmt
except ImportError:
from gruel import pmt

#
# This          hack forces a 'has-a' relationship to look like an 'is-a' one.
#
#          It allows Python classes to subclass this one, while passing through
#          method calls to the C++ class shared pointer from SWIG.
#
# It          also allows us to intercept method calls if needed
#
class          hier_block2(object):
"""
Python wrapper around          the C++ hierarchical block implementation.
Provides convenience          functions and allows proper Python subclassing.
"""

def          __init__(self, name, input_signature, output_signature):
"""
Create          a hierarchical block with a given name and I/O signatures.
"""
self._hb          = hier_block2_swig(name, input_signature, output_signature)

def          __getattr__(self, name):
"""
Pass-through member          requests to the C++ object.
"""
if not          hasattr(self, "_hb"):
raise RuntimeError("hier_block2:          invalid state--did you forget to
call gr.hier_block2.__init__ in a          derived class?")
return getattr(self._hb, name)

def          connect(self, *points):
"""
Connect two or more          block endpoints. An endpoint is either a (block,
port)
tuple or          a block instance. In the latter case, the port number is
assumed
to          be zero.

To connect the hierarchical block external inputs or          outputs to internal
block
inputs or outputs, use 'self' in the          connect call.

If multiple arguments are provided, connect will          attempt to wire them in
series,
interpreting the endpoints as          inputs or outputs as appropriate.
"""

if len          (points) < 1:
raise ValueError, ("connect requires at least one          endpoint; %d
provided." % (len (points),))
else:
if          len(points) == 1:
self._hb.primitive_connect(points[0].to_basic_block())
else:
for          i in range (1, len (points)):
self._connect(points[i-1], points[i])

def          _connect(self, src, dst):
(src_block, src_port) =          self._coerce_endpoint(src)
(dst_block, dst_port) =          self._coerce_endpoint(dst)
self._hb.primitive_connect(src_block.to_basic_block(),          src_port,
dst_block.to_basic_block(), dst_port)

def          _coerce_endpoint(self, endp):
if hasattr(endp, 'to_basic_block'):
return          (endp, 0)
else:
if hasattr(endp, "__getitem__") and len(endp) ==          2:
return endp # Assume user put (block, port)
else:
raise          ValueError("unable to coerce endpoint")

def          disconnect(self, *points):
"""
Disconnect two          endpoints in the flowgraph.

To disconnect the hierarchical          block external inputs or outputs to
internal block
inputs or          outputs, use 'self' in the connect call.

If more than two          arguments are provided, they are disconnected
successively.
"""

if          len (points) < 1:
raise ValueError, ("disconnect requires at          least one endpoint; %d
provided." % (len (points),))
else:
if          len (points) == 1:
self._hb.primitive_disconnect(points[0].to_basic_block())
else:
for          i in range (1, len (points)):
self._disconnect(points[i-1],          points[i])

def _disconnect(self, src, dst):
(src_block,          src_port) = self._coerce_endpoint(src)
(dst_block, dst_port) =          self._coerce_endpoint(dst)
self._hb.primitive_disconnect(src_block.to_basic_block(),          src_port,
dst_block.to_basic_block(), dst_port)

def          msg_connect(self, src, srcport, dst, dstport):
self.primitive_msg_connect(src.to_basic_block(),          srcport,
dst.to_basic_block(), dstport);

def          msg_disconnect(self, src, srcport, dst, dstport):
self.primitive_msg_disconnect(src.to_basic_block(),          srcport,
dst.to_basic_block(), dstport);

def          message_port_register_hier_in(self, portname):
self.primitive_message_port_register_hier_in(pmt.pmt_intern(portname));

def          message_port_register_hier_out(self, portname):
self.primitive_message_port_register_hier_out(pmt.pmt_intern(portname));
```
i          have been unable to find any sort of solution to this problem          anywhere. Any help will be greatly appreciated.
Thank you very much!

---


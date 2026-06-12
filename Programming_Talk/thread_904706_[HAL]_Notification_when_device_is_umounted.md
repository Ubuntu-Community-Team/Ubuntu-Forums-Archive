---
title: "[HAL] Notification when device is umounted"
date: 2008-08-29
forum: Programming Talk
---

### Post by Xenesis on 2008-08-29
Hello,
i am writing a program that takes care of all the removable devices that are connected to the computer. It will become a panel applet that should allow easy mounting/umounting like in windows the "save remove" function in the taskbar.
The program is written in Python.
As a start I took the code from [https://dfwpython.org/repo/Projects/DBUS/dtest.py](https://dfwpython.org/repo/Projects/DBUS/dtest.py).
I have now a HalManager and a hall device class that can recognize, when a device is (physically) added or removed from the computer.
However I have no working code that will notify me, when a volume is mounted or unmounted.

According to [http://people.redhat.com/davidz/hal-spec/hal-spec.html#device-properties-volume](http://people.redhat.com/davidz/hal-spec/hal-spec.html#device-properties-volume) I would have to listen for the Condition VolumeMount/VolumeUnmount.
My Problem is now: How can I listen for such conditions. At this point I have this code to listen for conditions:

```

class HalDevice(object):

	INTERFACE = 'org.freedesktop.Hal.Device'

	def __init__(self, udi):
		bus      = dbus.SystemBus()
		self.dev_obj  = bus.get_object(HalManager.SERVICE, udi)
        	self.dev = dbus.Interface(self.dev_obj, HalDevice.INTERFACE)
        	self.udi = udi

		self.dev.connect_to_signal('PropertyModified', self.property_modified)
		self.dev.connect_to_signal('Condition', self.condition_occurred)

		self.properties = self.HalDevicePropertiesMapping(self)
		self.capabilities = self.HalDeviceCapabilitiesSet(self)

	def condition_occurred(self, condition, *args, **kwargs):
		"""
		Notification handler that receives information about the occurrence of
		a non-property event.

		Normally this is used to signal events that aren't or can't be
		expressed in properties, e.g. 'ProcessorOverheating' etc.

	"""
		print "condition_occurred for "  + self.udi
		print "condition = " + str(key)
		print "args = " + str(args)
		print "kwargs = " + str(kwargs)
		pass

```

However, if i mount a volume, the function condition_occured is never called.
Can you tell me what I have to do, to get a notification when a volume is mounted or unmounted

Thanks!

---

### Post by PinguinNordpol on 2008-09-01
Hi

I have pretty much the same problem, but am writing my application in C.
I too studied the HAL specs and reasoned that it should be possible to listen to the VolumeMount device condition by providing a callback through libhal_ctx_set_device_condition. But this callback is never called when I mount a volume nor can I see any VolumeMount signal using dbus-monitor.

Could someone please tell me why this isn't working?

```
#include <stdio.h>
#include <hal/libhal.h>
#include <dbus/dbus.h>
#include <dbus/dbus-glib.h>

static void device_condition(LibHalContext *ctx,
                             const char *udi,
                             const char *condition_name,
                             const char *condition_detail)
{
  // Just to see if I ever receive this signal
  printf("--> Device condition occured: Name: %s Detail: %s\n",condition_name,condition_detail);
}

int main(int argc, char **argv)
{
  static LibHalContext *ctx;
  DBusError dbus_error;
  DBusConnection *dbus_conn;
  GMainLoop *loop;
  char **devices;
  int nr;

  ctx = libhal_ctx_new();
  if (ctx == NULL) {
    g_warning("Could not create HAL context\n");
  }

  dbus_error_init(&dbus_error);
  dbus_conn = dbus_bus_get (DBUS_BUS_SYSTEM, &dbus_error);

  if (dbus_error_is_set(&dbus_error)) {
    g_warning("Could not connect to system bus %s\n", dbus_error.message);
  }
  dbus_connection_setup_with_g_main (dbus_conn, NULL);
  dbus_connection_set_exit_on_disconnect (dbus_conn, FALSE);

  libhal_ctx_set_dbus_connection(ctx, dbus_conn);

  libhal_ctx_set_device_condition(ctx, device_condition);

  if (!libhal_ctx_init (ctx, &dbus_error)) {
    warn ("libhal_ctx_init failed: %s", dbus_error.message);
    dbus_error_free (&dbus_error);
    libhal_ctx_free (ctx);
    return 1;
  }
  if (!(devices = libhal_get_all_devices (ctx, &nr, &dbus_error))) {
    warn ("hald not running: %s", dbus_error.message);
    dbus_error_free (&dbus_error);
    libhal_ctx_shutdown (ctx, NULL);
    libhal_ctx_free (ctx);
    return 1;
  }

  // main loop
  loop = g_main_new(FALSE);
  g_main_run(loop);

  libhal_ctx_free(ctx);
}
```

---

### Post by juannm on 2009-02-03
Hi, I'm also interested in this stuff, for the previous posters you should know that the reason about your callback functions not being called is that HAL doesn't even seem to emit any "Condition" signal.

For example, by running the dbus-monitor program as the following:
```
$ dbus-monitor --system "type='signal',sender='org.freedesktop.Hal',interface='org.freedesktop.Hal.Device'"
```

or even

```
$ dbus-monitor --system "type='signal',interface='org.freedesktop.Hal.Device'"
```

you can see that no Condition signal is emitted. So I think this is a bug in Hal.

Using Ubuntu Hardy (because it is the last LTS if i'm not wrong).

---

### Post by mattijohn on 2009-03-25
Hi,

I've been looking into this as well and haven't tried it yet, but according to the specs the DeviceAdded signal from the org.freedesktop.Hal.Manager interface should be what you're looking for

[http://people.freedesktop.org/~david/hal-spec/hal-spec.html](http://people.freedesktop.org/~david/hal-spec/hal-spec.html)

---

### Post by imdano on 2009-03-25
> **mattijohn said:**
> Hi,

I've been looking into this as well and haven't tried it yet, but according to the specs the DeviceAdded signal from the org.freedesktop.Hal.Manager interface should be what you're looking for

[http://people.freedesktop.org/~david/hal-spec/hal-spec.html](http://people.freedesktop.org/~david/hal-spec/hal-spec.html)Correct, DeviceAdded and DeviceRemoved are what you want.

---


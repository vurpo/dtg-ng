# What is this?

I did a few tweaks to the https://github.com/Maccraft123/dtg-ng repo to at least get it to build. It's still pretty messy, though.

## Dependencies (Debian/Ubuntu)

The following deps should be installed to build this on Debian or Ubuntu.

```
# apt install build-essential g++-10 git meson libarchive-tools libssl-dev debootstrap
# apt build-dep mesa
# apt build-dep xwayland
```

## Creating an SD card image

This script has been tweaked to work with a loop mounted image file rather than writing straight to an SD card.

Create an empty image file (TODO check what size image? `8G` created an image file too big to fit on an 8 GB SD card, so IDK):

```
$ fallocate -l 7G image.img
```

Set up the empty image file as a loop device, and make note of the device name it outputs:

```
# losetup -f --show image.img
/dev/loopX
```

Now use this device name as the SD card device path when running the `build-all` script (only argument to the script) or when running the individual build scripts.


## RKDeveloptool
RKDeveloptool gives you a simple way to read/write rockusb device.  
Let's start.

## Compile and install
### MacOsX
    brew install libusb
    make
    make install

### Linux
first install pkg-config, libusb and libudev

    sudo apt-get install pkg-config libudev-dev libusb-1.0 libusb-1.0-0-dev 
    make 
    make install  
    


## Usage
input `rkdeveloptool -h` to see
```
---------------------Tool Usage ---------------------
Help:			-h or --version
Version:		-v or --version
DownloadBoot:		db <Loader>
UpgradeLoader:		ul <Loader>
ReadLBA:		rl  <BeginSec> <SectorLen> <File>
WriteLBA:		wl  <BeginSec> <File>
WriteLBA:		wlx  <PartitionName> <File>
WriteGPT:		gpt <gpt partition table>
PrintGPT:		pgpt 
EraseFlash:		ef 
TestDevice:		td
ResetDevice:		rd [subcode]
ReadFlashID:		rid
ReadFlashInfo:		rfi
ReadChipInfo:		rci
PackBootLoader:		pack
UnpackBootLoader:	unpack <boot loader>
TagSPL:			tagspl <tag> <U-Boot SPL>
-------------------------------------------------------
```

example: download kernel.img

```bash
  sudo ./rkdeveloptool db RKXXLoader.bin    //download usbplug to device
  sudo ./rkdeveloptool wl 0x8000 kernel.img //0x8000 is base of kernel partition,unit is sector.
  sudo ./rkdeveloptool rd                   //reset device
```

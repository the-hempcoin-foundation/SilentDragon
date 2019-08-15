# HempPay

HempPAY desktop wallet for THC ($THC) runs on Linux, Windows and macOS.
This is experimental software under active development!

![Screenshots](hemppay.png?raw=true)

## PRIVACY NOTICE

HempPAY contacts a few different external websites to get various
bits of data.
    * coingecko.com for price data API
    * XXX for explorer links
    * dexstats.info for address utilities

This means your IP address is known to these servers. Enable Tor setting
in HempPAY to prevent this, or better yet, use TAILS: https://tails.boum.org/

# Installation

Head over to the releases page and grab the latest installers or binary. XXXX

## thcd

HempPay needs a Hush full node running. If you already have a full node running, this wallet will connect to it.

If you don't have one, HempPay will start its embedded komodod node.

Additionally, if this is the first time you're running HempPAY or a komodod daemon, HempPAY will find Sapling params (~50 MB) and configure `HUSH3.conf` for you. 

Pass `--no-embedded` to disable the embedded komodod and force HempPAY to connect to an external node.

## Compiling from source

HempPAY is written in C++ 14, and can be compiled with g++/clang++/visual
c++. It also depends on Qt5, which you can get from
[here](https://www.qt.io/download). Note that if you are compiling from source,
you won't get the embedded komodod by default. You can either run an external
komodod, or compile komodod as well.


### Building on Linux

```
sudo apt-get install qt5-default qt5-qmake libqt5websockets5-dev
git clone https://github.com/the-hempcoin-foundation/HempPAY.git
cd HempPAY
qmake hemppay.pro CONFIG+=debug
make -j$(nproc)

./hemppay
```

### Building on Windows
You need Visual Studio 2017 (The free C++ Community Edition works just fine). 

From the VS Tools command prompt
```
git clone  https://github.com/the-hempcoin-foundation/HempPAY.git
cd HempPAY
c:\Qt5\bin\qmake.exe hemppay.pro -spec win32-msvc CONFIG+=debug
nmake

debug\HempPAY.exe
```

To create the Visual Studio project files so you can compile and run from Visual Studio:
```
c:\Qt5\bin\qmake.exe hemppay.pro -tp vc CONFIG+=debug
```

### Building on macOS
You need to install the Xcode app or the Xcode command line tools first, and then install Qt. 

```
git clone https://github.com/the-hempcoin-foundation/HempPAY.git
cd HempPAY
qmake hemppay.pro CONFIG+=debug
make

./HempPAY.app/Contents/MacOS/HempPAY
```

### Emulating the embedded node

In binary releases, HempPAY will use node binaries in the current directory to sync a node from scratch.
It does not attempt to download them, it bundles them. To simulate this from a developer setup, you can symlink
these four files in your Git repo:

```
    ln -s ../komodo/src/komodod
    ln -s ../komodo/src/komodo-cli
```

The above assumes HempPAY and komodo git repos are in the same directory. File names on Windows will need to be tweaked.

### Support

...

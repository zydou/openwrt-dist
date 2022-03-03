# My Personal OpenWRT dist
[![](https://github.com/zydou/openwrt-dist/workflows/Package%20Builder/badge.svg)](https://github.com/zydou/openwrt-dist/actions)
[![](https://github.com/zydou/openwrt-dist/workflows/Image%20Builder/badge.svg)](https://github.com/zydou/openwrt-dist/actions)

Daily build with GitHub Actions.

This project is only for OpenWRT routers of x86_64 architecture. Currently it's based on 2102.

[You may want original project here.](https://github.com/simonsmh/openwrt-dist)

## Openwrt Packages

### Usage
#### Step 1
First, Add the public key [key-build.pub](./key-build.pub) which is paired with private key [key-build](./key-build) for building.

```
wget http://cdn.jsdelivr.net/gh/zydou/openwrt-dist@master/key-build.pub
opkg-key add key-build.pub
```

#### Step 2
Add the following lines to `/etc/opkg/customfeeds.conf`.

```
src/gz zydou http://cdn.jsdelivr.net/gh/zydou/openwrt-dist@packages/x86/64
src/gz passwall http://cdn.jsdelivr.net/gh/zydou/openwrt-dist@passwall/x86/64
```

Then install whatever you want.

```
opkg update
opkg install mentohust
opkg install luci-app-openclash
opkg install luci-app-passwall
opkg install ChinaDNS
opkg install luci-app-chinadns
opkg install dns-forwarder
opkg install luci-app-dns-forwarder
opkg install shadowsocks-libev
opkg install luci-app-shadowsocks
opkg install v2ray-plugin
opkg install luci-app-pdnsd
opkg install v2ray-core
opkg install luci-app-v2ray
opkg install luci-app-vlmcsd
...
```

Please check the manifest for more detail .

You can also search and install them in LuCI or upload these downloaded files to your router with SCP/SFTP, then ssh to your router and use opkg to install these ipk files.

## Openwrt Image Firmwares

There are some precompiled firmwares under [`image/generic.x86_64`](https://github.com/zydou/openwrt-dist/tree/image/generic.x86_64) branch.

Here are the built-in packages:
- mentohust
- openclash
- passwall

You can check the [official documentation](https://openwrt.org/docs/guide-user/installation/openwrt_x86) to choose the firmware format you need.

## License
GPLv3

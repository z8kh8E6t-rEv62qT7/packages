# SPDX-License-Identifier: GPL-3.0-only
#
# Copyright (C) 2022-2023 ImmortalWrt.org

include $(TOPDIR)/rules.mk

PKG_NAME:=sing-box
PKG_VERSION:=1.13.19
PKG_RELEASE:=1

SING_BOX_ARCH_HASHES:= \
	aarch64_cortex-a53=55cd213e8f524be4c9ddadc45f2d3202531c6179ba76bee5ecea9d64fd1b251f \
	aarch64_cortex-a72=001cb6cc7d077597857ea458c8143eeb541835a32f73709cf601476ea9c18e04 \
	aarch64_cortex-a76=c47f524be98198dfb93954bf559b541530c67a7e8fc6b2a3085c6b9cf42752af \
	aarch64_generic=c1c31aab36dca5bbc83488e6f7412b1f402c0639f43f62512ae2a56e268a0dc5 \
	arm_arm1176jzf-s_vfp=e22caf2e9d3d6037bf0a397d9f1bfd9439be0ff0e8f78017376229f115f26ab7 \
	arm_arm926ej-s=f553965356fdfdcbf44c532588ee175279d7dc13737fb1e7f3c50432afd35dfc \
	arm_cortex-a15_neon-vfpv4=3c92d85de03f3588985d66de55c14334090131351ecdd2e83606e730cd42f472 \
	arm_cortex-a5_vfpv4=8f74a4f86b7fd43f980c95022d87a9c3a05ca6ce3d23ca24105ed97d9f5fc385 \
	arm_cortex-a7=91470e3e654cc426484d26565b356b228f5abf1b1a4d5a817f34ae3e4f777f02 \
	arm_cortex-a7_neon-vfpv4=450f745f694fd0933058361402988834d3735bae7df623da9538507169665407 \
	arm_cortex-a7_vfpv4=4ffec5cd6b64dee25511eb6eb7083b05a98d880c84014ec0fbcafac1728e536a \
	arm_cortex-a8_vfpv3=d6d41f508185197f27a7a2b298647690193eff1446f65a1759eebb7ebd5a9541 \
	arm_cortex-a9=e10151141924849795bae3255508926825ba773dc97c0654e9ff75530a3fcde2 \
	arm_cortex-a9_neon=86bdf55d7cb2b46cd909056ff7d4e612a60a004abab5177c791d1979f5b91a92 \
	arm_cortex-a9_vfpv3-d16=cb33c522449d97e36381fa74231483ae88e4f9f66c9425ec17bed61bd16e4a65 \
	arm_fa526=cf6f22b34f05ac8868990acdbbdc91a5a123ecfe20a366186c233d7cffb2db71 \
	arm_xscale=04e4b5fe3c35f4227f932ebaea8384a9561b18685f5717923766711fc12e8043 \
	i386_pentium-mmx=25c7ded9e1e5d1481d9bb9d908957cbdeed3ea018f31f1ccc7df742d0ab35479 \
	i386_pentium4=dc4c34cdccacab005ae47a3e971f4eb5e5c613590e7ca7d1a440a742f0befae3 \
	loongarch64_generic=00c2ea15c7fc2be8bb583cb2576fbefa2a636a2bc59abd8ad1501d30d2e69306 \
	mips64el_mips64r2=41d04e70f596ed7b56c51ee9bfb17a7a13834273d844df4a786f3f35e3c15f60 \
	mips64_mips64r2=78457c95c6fb78ca9787ed91b269312082f00875eb20ddd7d24300936f4f223e \
	mips64_octeonplus=5c9ead612f89244f2228d2acf524cc0e7ad98ba60b5a8820ef455b039efb1704 \
	mipsel_24kc=ea355c77c2ad9ac5e2dcc3e467abd7a90dff0047d49989e41a8b4c9c3cc57c11 \
	mipsel_24kc_24kf=40b8e30f59d38b9715ae210a678e42786b63857567102689bf1cc8782fe33197 \
	mipsel_74kc=c28654c16f2c322dd1b5c21340f6510efd337a95efea3f168924918f44b7c2b4 \
	mipsel_mips32=04b826f5d47ac754f6df9b2c70840811a3bb4074dab12cbdd36fb0240a5a45d4 \
	mips_24kc=c0e45f92b6c8d8fddb0e325e6d20e07aecc94e8e4653b13509290f28f94266a3 \
	mips_4kec=8459ca3d554dec57f318d9797cd15d346243eac96dedf1e129293a6d5e476d97 \
	mips_mips32=b679d7f74eb53088a2cb58a19cea0e43fcb86d8accc0fd2017bd5e54b42fdca2 \
	riscv64_generic=59e8139f314e1cc7d98258ee2ef3acf5d21ecc629cba1d1885ae7312f8805c1e \
	x86_64=0ab15ab6ee3addc64bd6a85295cdbc9f85b48e4522543ef4e7764ca89699dbf2

SING_BOX_ARCH_DEPENDS:=@(aarch64||arm||i386||i686||loongarch64||mips||mips64||mips64el||mipsel||riscv64||x86_64)

PKG_SOURCE:=$(PKG_NAME)_$(PKG_VERSION)_openwrt_$(ARCH_PACKAGES).ipk
PKG_SOURCE_URL:=https://github.com/SagerNet/sing-box/releases/download/v$(PKG_VERSION)
PKG_HASH:=$(patsubst $(ARCH_PACKAGES)=%,%,$(filter $(ARCH_PACKAGES)=%,$(SING_BOX_ARCH_HASHES)))

ifneq ($(CONFIG_PACKAGE_sing-box),)
  ifeq ($(PKG_HASH),)
    $(error sing-box v$(PKG_VERSION) has no official OpenWrt build for ARCH_PACKAGES=$(ARCH_PACKAGES))
  endif
endif

PKG_LICENSE:=GPL-3.0-or-later
PKG_MAINTAINER:=Tianling Shen <cnsztl@immortalwrt.org>

include $(INCLUDE_DIR)/package.mk

define Package/sing-box
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Web Servers/Proxies
  TITLE:=The universal proxy platform
  URL:=https://sing-box.sagernet.org/
  DEPENDS:=$(SING_BOX_ARCH_DEPENDS) +ca-bundle +kmod-inet-diag +kmod-tun +firewall4 +kmod-nft-queue
  USERID:=sing-box=5566:sing-box=5566
endef

define Package/sing-box/description
  Sing-box is a universal proxy platform which supports hysteria, SOCKS, Shadowsocks,
  ShadowTLS, Tor, trojan, VLess, VMess, WireGuard and so on.
endef

define Build/Prepare
	$(HOST_TAR) -xzOf $(DL_DIR)/$(PKG_SOURCE) data.tar.gz | \
		$(HOST_TAR) -xzf - -C $(PKG_BUILD_DIR) ./usr/bin/sing-box
endef

define Build/Compile
endef

define Package/sing-box/conffiles
/etc/config/sing-box
/etc/sing-box/
endef

define Package/sing-box/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/usr/bin/sing-box $(1)/usr/bin/sing-box

	$(INSTALL_DIR) $(1)/etc/sing-box
	$(INSTALL_DATA) ./files/config.json $(1)/etc/sing-box/config.json

	$(INSTALL_DIR) $(1)/etc/config/
	$(INSTALL_CONF) ./files/sing-box.conf $(1)/etc/config/sing-box
	$(INSTALL_DIR) $(1)/etc/init.d/
	$(INSTALL_BIN) ./files/sing-box.init $(1)/etc/init.d/sing-box
endef

$(eval $(call BuildPackage,sing-box))

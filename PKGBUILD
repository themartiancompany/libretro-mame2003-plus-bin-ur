# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer:
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

_os="$( \
  uname \
    -o)"
_evmfs_available="$( \
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
_pkg="mame2003-plus"
_pkgname="libretro-${_pkg}"
_Pkg="MAME2003-plus"
pkgname="${_pkgname}-bin"
pkgver="0.139"
pkgrel=1
_pkgdesc=(
  "RetroArch backend for"
  "the '2003 Plus'"
  "version of MAME"
  "multi-purpose"
  "emulation framework."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'arm'
  'armv7l'
)
_http="https://github.com"
_ns="libretro"
url="${_http}/${_ns}/${_pkg}-libretro"
license=(
  'custom:MAME License'
)
depends=(
  'retroarch'
)
if [[ "${_os}" != "GNU/Linux" ]] && \
   [[ "${_os}" == "Android" ]]; then
  depends+=(
    'inteppacman'
  )
fi
optdepends=(
)
if [[ "${_os}" != "GNU/Linux" ]] && \
   [[ "${_os}" == "Android" ]]; then
  optdepends+=(
  )
fi
makedepends=(
  'coreutils'
)
if [[ "${_evmfs}" == "true" ]]; then
  makedepends+=(
    'evmfs'
  )
fi
checkdepends=(
)
provides=(
  "${_pkgname}=${pkgver}"
)
conflicts=(
  "${_pkgname}"
)
source=()
sha256sums=()
_lib="mame2003_plus_libretro_android"
# This file has been published onto Ethereum Holesky testnet.
# That network may disappear sooner or later, so you'll have to crowd-publish it
# onto mainnets download after download on the mainnets when crowd-publishing
# will be ready.
_evmfs_network="7001"
_evmfs_address="0x151920938488F193735e83e052368cD41F9d9362"
# The kid
_evmfs_ns="0x926acb6aA4790ff678848A9F1C59E578B148C786"
# Truocolo
_evmfs_sig_ns="0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b"
_lib_sum="b5c7f02c4bd973597310afc3e5d95bd369a3c7b9ea7736093ac6ff830443be08"
_lib_sig_sum="f9f3ef1c8cadef0836375cceb5586f31babd4c27cf0bc3a6947a12905a1eacd6"
_http="https://github.com"
_ns="6xrS42VaMBgMbWRPAiVP"
_url="${_http}/${_ns}/${pkgname}"
_commit="b78946661c419a1fefe927cacc5619dccec4ace0"
_evmfs_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_lib_sum}"
if [[ "${_evmfs}" == "true" ]]; then
  _lib_src="${_lib}.arm.so.tar.xz::${_evmfs_uri}"
elif [[ "${_evmfs}" == "false" ]]; then
  _lib_src="${_lib}.arm.so.tar.xz::${_url}/raw/${_commit}/${_lib}.arm.so.tar.xz"
fi
source+=(
  "${_lib_src}"
)
sha256sums+=(
  "${_lib_sum}"
)

validgpgkeys=(
  # Truocolo
  #   <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  #   <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
  'F690CBC17BD1F53557290AF51FC17D540D0ADEED'
  # Pellegrino Prevete (dvorak)
  #   <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'
)

package() {
  local \
    _dest_dir
  _dest_dir="/data/data/com.retroarch/cores"
  install \
    -dm755 \
    "${pkgdir}${_dest_dir}"
  install \
    -Dm644 \
    "${srcdir}/${_lib}" \
    "${pkgdir}/${_dest_dir}/${_lib}"
}

# vim: ft=sh syn=sh et

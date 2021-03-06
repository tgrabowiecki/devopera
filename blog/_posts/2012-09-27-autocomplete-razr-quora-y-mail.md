---
title: Autocomplete, Razr, Quora, Y!Mail
authors:
- ola-kleiven
tags:
- sitepatching
license: cc-by-3.0
---

## Added patches

`fixJQueryAutocomplete()` — generic patch to fix the browser sniffing in the obsolete autocomplete plugin for jQuery. Widely used and breaks after we fixed key event handling in Opera. 12.10+

- PATCH-876, razr.com: CSS `url()` argument takes quotes according to CSSOM, but not all browsers do it that way, so we patch.
- PATCH-874, Fix transition event case to un-confuse jQuery. A bit unfortunate renaming of event in Opera causes some breakage here and there. 12.0x only, as 12.10+ has removed prefixes.
- PATCH-871, udemy.com: work around lack of pointer-events for non-SVG content in Opera.
- PATCH-873, onlystudy.cn: make sure an event is passed in to the handler.
- PATCH-863, Throttle scroll events and certain timeouts to improve Quora performance. Quora is still misbehaves in 12.0x due to other Core issues. Should be better in 12.10.
- PATCH-862, hipmunk.com: avoid header table cell collapse. Core bug.
- PATCH-794, Prevent broken `innerHTML` setter on Disney booking site.

## Changed patches

PATCH-325, Y!Mail sniffing. Regional sites use different “browser not supported” screens, try to catch more of them.

## Removed patches

PATCH-261, Hide broken implementation of `showModalDialog` to make object detection reliable. The broken implementation will be removed in 12.10. May re-surface at some point, who knows.

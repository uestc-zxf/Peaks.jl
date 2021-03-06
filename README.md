# Peaks.jl

[![Build Status](https://travis-ci.com/halleysfifthinc/Peaks.jl.svg?branch=master)](https://travis-ci.com/halleysfifthinc/Peaks.jl)
[![codecov](https://codecov.io/gh/halleysfifthinc/Peaks.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/halleysfifthinc/Peaks.jl)
![Maintenance](https://img.shields.io/maintenance/yes/2020)



Peaks.jl contains peak (local extrema) finding functions for vector data. Contributions welcome.

## Functions

- `maxima`/`minima`
  - Find the indices of the local extrema of `x` where each extrema is
    either the maximum of `x[-w:w]` or the first index of a plateau.
    If `strictbounds` is `true`, all elements of `x[-w:w]` must exist
    and may not be `missing` or `NaN`. If `strictbounds` is `false`,
    elements of `x[-w:w]` may not exist (eg peaks may be less than `w`
    indices from either end of `x`), or may be `missing` or `NaN`.
    `missing` or `NaN` must not be extrema.
  - Supports OffsetArrays
  - See docstring for more information

- `peakprom`
  - Find all local extrema and peak prominences in `x` matching the
    conditions `w` and `minprom`. `w` sets the minimum allowed distance
    between extrema. `minprom` sets the minimum prominence (inclusive) of
    returned extrema.
    Peak prominence is calculated as the difference between the current
    extrema and the most extreme of the smallest extrema of the lower and upper
    bounds. Bounds extend from the current extrema to the next extrema
    more extreme than the current extrema, or the end of the signal,
    which ever comes first.
  - Does not currently support `strictbounds = false`
  - See docstring for more information

## Related

- [**Images.jl**](https://github.com/JuliaImages/Images.jl)
  - [`findlocalmaxima`](https://juliaimages.org/stable/function_reference/#Images.findlocalmaxima)/[`findlocalminima`](https://juliaimages.org/stable/function_reference/#Images.findlocalminima)
    - Supports more than 1 dimension
    - Doesn't support `missing`, different window sizes

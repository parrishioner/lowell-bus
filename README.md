# Lowell Bus Simulator

A simple static web tool for simulating morning bus/train transfer times to school.

Pick a route, choose how many simulations to run (up to 1000), and it runs the
simulation across every scheduled first-leg departure time, showing stats like
percent arriving comfortably on time, cutting it close, or late, plus which
transfer bus/train ends up getting caught.

## Usage

Just open `index.html` in a browser — no build step, no server, no dependencies.

## How it works

- Each route is defined in `index.html` as a first leg (e.g. a bus or train)
  and one or more second-leg options serving the same transfer stop. The
  simulation picks whichever second-leg trip arrives first after accounting
  for the transfer walk.
- Delays are modeled as independent random jitter per bus/train leg (a normal
  distribution, mean +2 min late, floored at -2 min early). Walking segments
  are treated as fixed.
- School start time and the "comfortably on time" buffer are constants near
  the top of the script (`SCHOOL_START`, `COMFORTABLE_BUFFER_MINS`) — easy to
  change in one place.

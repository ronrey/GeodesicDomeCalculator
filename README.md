# Geodesic Dome Calculators

Two interactive calculators for designing geodesic domes based on icosahedral subdivision. Both tools run entirely in the browser with no dependencies or build steps required.

## Tools

### 1. GeodesicDomeCalculator.html
Basic geodesic dome calculator that computes strut lengths from a given diameter.

**Features:**
- Calculate unique strut lengths for Class I icosahedral domes
- Adjustable frequency (1V to 10V)
- Hemisphere or full sphere cuts
- Configurable grouping tolerance
- 3D interactive visualization with color-coded strut types
- Export strut lengths and panel data to CSV
- Multiple unit systems (feet, inches, meters, millimeters)

**Use case:** Planning material requirements for dome construction where all struts are cut from uniform material.

### 2. GeodesicStrutCalc.html
Advanced calculator for wood panel domes with beveled edges.

**Features:**
- Calculates outer and inner strut lengths for panels with thickness
- Computes bevel angles (dihedral angles) for proper edge fitting
- Dual-layer visualization showing both outer and inner strut networks
- Panel composition analysis grouped by edge types
- Separate toggles for outer/inner strut visibility
- Export detailed CSV files with centerline, outer, inner lengths and bevels
- Fullscreen visualization mode

**Use case:** Building domes from flat panels (plywood, etc.) that butt together along beveled edges, where you need different lengths for the outer and inner surfaces.

## Quick Start

1. Download either HTML file
2. Open it in a modern web browser (Chrome, Firefox, Safari, Edge)
3. Enter your dome specifications
4. View results in tables and 3D visualization
5. Download CSV files for construction reference

No installation, no server, no internet connection required after download.

## How It Works

Both calculators:
1. Generate an icosahedron (20-faced polyhedron)
2. Subdivide each triangular face based on frequency
3. Project vertices onto a sphere
4. Calculate chord lengths between connected vertices
5. Group similar lengths within a tolerance
6. Compute panel compositions and angles

**GeodesicStrutCalc.html** additionally:
- Calculates dihedral angles between adjacent panels
- Determines bevel angles (half the dihedral)
- Adjusts strut lengths for outer/inner surfaces based on panel thickness
- Uses the formula: `outerLength = midLength + thickness × tan(bevelAngle)`

## Understanding the Results

### Strut Types
Letters (A, B, C, etc.) identify unique strut lengths. The calculator groups struts within your specified tolerance to account for manufacturing precision.

### Frequency
- **2V**: ~2 strut types, simpler but larger panels
- **3V**: ~3 strut types, good balance
- **4V**: ~5 strut types, smaller panels, more complex
- Higher frequencies create smoother spheres but require more cuts

### Panel Composition
Panels are labeled by their edge types. For example:
- `A + A + B`: Triangle with two A-length edges and one B-length edge
- `3xC`: Equilateral triangle with three C-length edges

### Bevel Angles
In GeodesicStrutCalc.html, bevel angles show how much to tilt your saw blade when cutting panel edges. Panels meet at twice the bevel angle (the dihedral angle).

## Technical Notes

### Coordinate System
- Domes are built in 3D space with Z-axis pointing up
- Hemisphere mode filters vertices where z ≥ 0
- Full sphere mode includes all vertices

### Tolerance
Grouping tolerance determines which struts are considered "the same length." A smaller tolerance creates more unique strut types but higher precision. Typical values:
- Feet: 0.001 to 0.01 ft
- Millimeters: 0.1 to 1 mm

### Precision
Output precision adjusts automatically:
- Millimeters: 2 decimal places
- Meters: 4 decimal places
- Feet/inches: 3 decimal places

## Browser Compatibility

Tested and working on:
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

Requires HTML5 Canvas and ES6 JavaScript support.

## Controls

### 3D Visualization
- **Drag**: Rotate view
- **Scroll/Pinch**: Zoom in/out
- **Reset View**: Return to default angle
- **Top View**: Look straight down (Z-axis)
- **Side View**: Look from the side (equator level)

### Checkboxes (GeodesicStrutCalc.html)
- **Show outer struts**: Display outer surface (warm colors)
- **Show inner struts**: Display inner surface (cool colors)
- **Show vertices**: Display connection points

## CSV Export Format

### Struts CSV (GeodesicDomeCalculator.html)
```csv
Strut Type,Length (ft),Quantity
A,2.456,30
B,2.891,40
```

### Struts CSV (GeodesicStrutCalc.html)
```csv
Type,Centerline (ft),Outer (ft),Inner (ft),Bevel (deg),Quantity
A,2.456,2.458,2.454,1.23,30
B,2.891,2.894,2.888,2.45,40
```

### Panels CSV
```csv
Panel,Panels,Edges,Dihedral 1 (deg),Dihedral 2 (deg),Dihedral 3 (deg)
T1,20,A + A + B,10.50,10.50,15.30
```

## Construction Tips

1. **Start with frequency 3V or 4V** for a good balance of complexity and strength
2. **Set tolerance based on your cutting precision** (table saw: 0.01 ft, CNC: 0.001 ft)
3. **Print CSV files** as cutting lists for the shop
4. **Label struts as you cut** to avoid confusion during assembly
5. **For beveled panels**, cut bevels on the table saw at the calculated angles
6. **Test fit a few panels** before cutting all materials

## Mathematical Background

The calculators implement Class I geodesic subdivision, also known as "alternate" or "icosahedral" method. This is the most common approach used in dome construction.

- Base polyhedron: Regular icosahedron
- Subdivision: Triacon subdivision of each face
- Projection: Spherical (all vertices equidistant from center)
- Chord factors: Calculated as straight-line distances between projected vertices

For more information on geodesic mathematics, see:
- Hugh Kenner's "Geodesic Math and How to Use It"
- Buckminster Fuller's "Synergetics"

## License

MIT License - Feel free to use, modify, and distribute.

## Contributing

These are single-file HTML applications with no build process. To contribute:

1. Fork the repository
2. Edit the HTML file directly
3. Test in multiple browsers
4. Submit a pull request

## Known Limitations

- Maximum frequency limited to 10V (browser performance)
- Spherical projection only (no ellipsoid support)
- Class I subdivision only (no Class II or III)
- No hub/connector calculations
- No structural analysis or load calculations

## Safety Disclaimer

These calculators provide geometric measurements only. They do not account for:
- Structural loads (snow, wind, seismic)
- Material strength and safety factors
- Building codes and regulations
- Foundation requirements

**Always consult with a licensed structural engineer before building any structure people will occupy.**

## Acknowledgments

Based on the geodesic mathematics pioneered by R. Buckminster Fuller and refined by generations of dome builders.

## Questions?

Open an issue on GitHub or consult dome-building communities for construction advice.
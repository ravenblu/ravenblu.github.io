---
title: "Real-time Shadows"
date: 2021-10-23T15:42:26-07:00
tags: ["graphics", "rendering"]
summary: 3D graphics study notes
toc: true
---

## Shadow Mapping Basics

### Two-pass Approach
1. Generate the depth/shadow map (to a texture) from the light’s perspective.
2. Use the depth information to calculate shadows from the camera’s point of view.

### Two Issues

**1. Shadow discrepancy (shadow acne)**  
Because the shadow map is limited by resolution, multiple fragments can sample the same value from the depth map when they’re relatively far away from the light source, or the angle between the light and the surface is too small.

*   **Solution:** Add a small amount of shadow bias based on the surface angle towards the light.

**2. Aliasing (jagged edges)**  
**Industry solutions:**
*   Different LOD on the shadow map
*   Dynamic resolutions
*   Average the values

**Algorithms:**
*   [Omnidirectional Shadow Maps](https://learnopengl.com/Advanced-Lighting/Shadows/Point-Shadows)
*   [Cascaded Shadow Maps](https://learnopengl.com/Guest-Articles/2021/CSM)

---

## Real-time Shadow Mapping

**Percentage Closer Filtering (to create soft shadows)**
*   Anti-aliasing for shadow edges.
*   Filter small: sharper, large: softer.

**Complete PCSS algorithm:**
1.  **Blocker search:** get the avg blocker depth in a certain region. Blocker search can be constant or heuristics (better).
2.  **Pernumbra estimation:** use the blocker depth to determine filter size.
3.  **Percentage closer filtering.**

---

## Other notes
Multiple light sources? Process one by one.

---

## References
*   [Shadow Mapping](https://learnopengl.com/Advanced-Lighting/Shadows/Shadow-Mapping)
*   [Shadow Mapping Course - 1 (Chinese)](https://www.bilibili.com/video/BV1YK4y1T7yY?p=3)
*   [Shadow Mapping Course - 2 (Chinese)](https://www.bilibili.com/video/BV1YK4y1T7yY?p=4)
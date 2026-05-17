---
name: seedance-video-prompt
description: Writes structured Seedance video-generation prompts with image-reference anchoring, timecoded shot lists, identity-continuity rules, cinematic color grading, and natural-sound direction. Use when the user asks for help with Seedance prompts, AI video prompts, text-to-video scene descriptions, cinematic video prompts, or any request to script a short generated film shot-by-shot. Trigger whenever the user mentions Seedance, video generation, text-to-video, AI video, shot list, scene prompt, or wants to turn a still concept into a timed video brief — even if they don't say "Seedance" by name.
---

# Seedance video-prompt builder

Seedance is a reference-driven text-to-video model: it takes a written prompt plus one or two reference images and produces a short clip. This skill turns a rough scene idea into a production-grade Seedance prompt — image-anchored, timecoded, identity-stable, and cinematically directed.

## Anatomy of a Seedance prompt

Every prompt this skill produces has six layers. Include all six.

1. **Reference-image anchoring** — at the top, declare each `<<<image_n>>>` and state explicitly what it locks (appearance, wardrobe, color grade, environment, face, lighting).
2. **Timecoded shot list** — `[m:ss]` blocks describing camera, subject action, framing, and on-screen sound at each beat. Total length 10–15 s.
3. **Identity / continuity clause** — one tight paragraph at the end forbidding distortion, flickering, ghosting, or any drift in face, hair, wardrobe, or props.
4. **Color grade** — name a specific grade ("teal-to-black", "warm tungsten", "bleach bypass"). State at the top, restate in the closer.
5. **Sound design** — list only the diegetic sounds you want; explicitly negate music and crowd unless wanted. Seedance follows literal sound direction.
6. **Quality / framing closer** — a short closing line stating resolution, cinematic intent, and what this is *not* ("a film not an advertisement").

## Workflow

1. Confirm the user has (or wants placeholders for) reference images. Note what each one locks.
2. Sketch a 4–6 beat shot list across 10–15 seconds. Reserve time for the climactic action and a holding aftermath beat — don't cut on the impact frame.
3. For each beat, write camera + subject + sound on consecutive lines. Keep prose terse; Seedance over-interprets adjectives.
4. Append the continuity clause, color-grade restatement, sound rules, and quality closer as one consolidated final paragraph — not scattered through the beats.
5. Verify every `<<<image_n>>>` declared at the top is doing real work in the shot list.

## Quality checklist

- Each reference image is declared once at the top, not re-cited in every beat.
- Shot list times are monotonic and total ≤ 15 s.
- Continuity clause appears exactly once, at the end.
- Color grade is named at the top and restated in the closer.
- Sound is direction, not description ("sharp crack of the release", not "dramatic sound design").
- No marketing adjectives ("amazing", "stunning") — Seedance reads them as visual instructions and gets weird.

## Adapting the template

- **Different subject** — keep the rhythm (tension → detail → action → transition → impact → aftermath hold); swap verbs and the climactic sound.
- **Different duration** — at 10 s, fold the flight and aftermath into one beat; 15 s is the upper bound for current Seedance models.
- **Different mood** — pick a color grade that matches (teal-to-black for cold focus, amber-to-shadow for warmth, monochrome for stark drama).
- **Looser identity** — soften the continuity clause but keep the wardrobe and color-grade locks.

## Worked example: archery scene

A complete prompt that illustrates all six layers. Study the structure; don't ship it verbatim.

```
<<<image_1>>> is the wide shot reference — match the archer's exact
appearance, white kit, Olympic recurve bow, teal-to-black color grade,
dark reflective floor, and rim lighting.

<<<image_2>>> is the close-up reference — match the archer's exact face,
ocean blue eye, draw hand fingers, and bowstring detail. Same person
throughout.

[0:00]
Close-up of the archer's face in strict side profile. Ocean blue eye
locked forward on the target, unblinking. The taut bowstring runs
vertically beside her eye. Cold, focused, empty expression. Bowstring
creaking under maximum tension.

[0:05]
Camera drifts slowly down to her draw hand fingers gripping the bowstring
at the corner of her mouth — three fingers, knuckles white with tension,
every tendon visible. The arrow nock sharp in frame. The string at
absolute maximum load.

[0:09]
The release. Fingers open cleanly and instantly. Bowstring snaps forward
with explosive force. Audio: sharp crack of the release breaking the
silence.

[0:10]
Camera follows the arrow in flight across the dark void toward the target
— the arrow a thin dark line cutting through the teal atmosphere,
fletching spinning, shaft flexing.

[0:13]
Arrow strikes the exact gold centre of the target. Impact. Shaft quivers
violently. Audio: sharp deep thud of impact.

[0:15]
Camera holds on the arrow buried perfectly in gold, shaft vibration
slowly settling to stillness. Silence.

Stable identity throughout — same face, same hair, same white kit, same
bow in every moment. No distortion, no flickering, no ghosting. No music,
no crowd. Natural sound only — bowstring creak, crack of release, arrow
hiss, impact thud, silence. Teal-to-black cinematic color grade throughout.
4K ultra-high definition. Cinematic quality. This is a film not an
advertisement.
```

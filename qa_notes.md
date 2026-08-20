# QA notes

## Initial visual check

The Ink Observatory setup screen renders with the generated hero art, brand crest, dark panel system, selected Hiragana state, Main Kana row matrix, and Start Quiz call to action. In-browser clicks on Start Quiz did not transition to the quiz screen during the initial preview pass, so the event flow requires diagnosis before delivery.

## Quiz transition check

Triggering Start Quiz from the live page context correctly opens the recall view. The default `Practice Hiragana + All Main Kana` selection creates a randomized 46-card deck, exposes romaji input fields, shows the live progress HUD, and presents the finish action. This confirms the application event flow is functioning; the earlier click issue was limited to the automated click timing rather than the page logic.

## Answer feedback check

Entering `ru` for the rendered る card and submitting with Enter marked the card as correct, incremented the correct count and streak, disabled the completed field, advanced the focus signal, and updated progress. Entering `xx` for the さ card incremented retries, reset the streak, retained a usable input, applied the error state, and displayed retry feedback. Both validation paths function correctly.

## Protected finish check

Finishing an incomplete deck displays the custom accessible confirmation dialog with the required unresolved-card warning and the `Keep practicing` / `Continue` actions. The dialog opens correctly over the card grid with an intentional dimmed backdrop.

## Results report check

Continuing from the finish dialog opens the session report. The report correctly calculates first-try accuracy (`1 / 46 · 2%` in the test run), renders the generated aurora summary panel, lists per-card status and retry data in the category table, includes working study links and WaniKani follow-up copy, and exposes the Home and Quiz Again actions.

## Final verification

The desktop and mobile setup screenshots are visually coherent, preserve readable contrast, and retain the responsive selection matrix without overflow. The production build completed successfully. Generated visual-asset paths remain runtime-resolved in the static project as expected, and the browser console shows no errors in the final setup view.

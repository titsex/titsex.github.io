<script lang="ts">
    import { email, socials } from "$lib";
</script>

<svelte:head>
    <title>titsex</title>
</svelte:head>

<div class="container">
    <h1 class="title">titsex</h1>

    <div class="social-grid">
        {#each socials as social}
            <a href={social.link} target="_blank" class="social-card">
                <img src={social.icon} alt={social.title} class="social-icon" />
                <span class="social-title">{social.title}</span>
            </a>
        {/each}
    </div>

    <div class="email-container">
        <a href="mailto:{email}" class="email-link">
            {email}
        </a>
    </div>
</div>

<style>
    :global(body) {
        margin: 0;
        padding: 0;
        background: #000;
        color: white;
        font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
        min-height: 100dvh;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
        width: 100%;
    }

    .title {
        font-size: 3.5rem;
        margin-bottom: 1.5rem;
        background: linear-gradient(90deg, #ff8a00, #e52e71, #7928ca);
        -webkit-background-clip: text;
        background-clip: text;
        color: transparent;
        animation: gradientShift 6s ease infinite;
        background-size: 300% 300%;
    }

    .social-grid {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
        gap: 1rem;
        margin-bottom: 2rem;
        width: 100%;
        max-width: 100%;
        justify-items: center;
    }

    .social-card {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding: 1.2rem;
        border-radius: 10px;
        background: rgba(255, 255, 255, 0.08);
        backdrop-filter: blur(12px);
        border: 1px solid rgba(255, 255, 255, 0.15);
        transition: transform 0.3s ease, background 0.3s ease;
        text-decoration: none;
        color: white;
        width: 120px;
        max-width: 100%;
    }

    .social-card:hover {
        transform: translateY(-3px);
        background: rgba(255, 255, 255, 0.15);
    }

    .social-icon {
        width: 40px;
        height: 40px;
        margin-bottom: 0.5rem;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .social-title {
        font-size: 0.9rem;
        font-weight: 500;
    }

    .email-container {
        margin-top: auto;
    }

    .email-link {
        color: rgba(255, 255, 255, 0.7);
        text-decoration: none;
        font-size: 1rem;
        position: relative;
        transition: color 0.3s ease;
    }

    .email-link:hover {
        color: white;
    }

    .email-link::after {
        content: '';
        position: absolute;
        bottom: -2px;
        left: 0;
        width: 0;
        height: 1px;
        background: white;
        transition: width 0.3s ease;
    }

    .email-link:hover::after {
        width: 100%;
    }

    @keyframes gradientShift {
        0% {
            background-position: 0 50%;
        }
        50% {
            background-position: 100% 50%;
        }
        100% {
            background-position: 0 50%;
        }
    }

    @media (max-width: 600px) {
        .title {
            font-size: 2.5rem;
        }

        .social-grid {
            grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
            gap: 0.8rem;
        }

        .social-card {
            width: 100px;
        }
    }

    @media (max-width: 400px) {
        .social-grid {
            grid-template-columns: repeat(auto-fill, minmax(90px, 1fr));
            gap: 0.5rem;
        }

        .social-card {
            width: 80px;
        }
    }
</style>
